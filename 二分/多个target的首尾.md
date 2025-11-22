34. 在排序数组中查找元素的第一个和最后一个位置

中等


给你一个按照非递减顺序排列的整数数组 nums，和一个目标值 target。请你找出给定目标值在数组中的开始位置和结束位置。

如果数组中不存在目标值 target，返回 [-1, -1]。

你必须设计并实现时间复杂度为 O(log n) 的算法解决此问题。

 

示例 1：

输入：nums = [5,7,7,8,8,10], target = 8
输出：[3,4]

示例 2：

输入：nums = [5,7,7,8,8,10], target = 6
输出：[-1,-1]

示例 3：

输入：nums = [], target = 0
输出：[-1,-1]


class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        res1 = -1
        res2 = -1
        l = 0
        r = len(nums) - 1
        while l <= r:
            mid = (l + r) // 2
            if nums[mid] == target:
                res1 = mid   //这是关键，相等就把这个当左边界，然后用r =mid -1 
                r = mid - 1  //这样到最后不相等的时候上一个res1 = mid就是最左
            elif nums[mid] > target:
                r = mid - 1
            elif nums[mid] < target:
                l = mid + 1
        l = 0
        r = len(nums) - 1
        while l <= r:
            mid = (l + r) // 2
            if nums[mid] == target:
                res2 = mid   //这是关键，相等就把这个当右边界，然后用l =mid +1 
                l = mid + 1  //这样到最后不相等的时候上一个res2 = mid就是最右
            elif nums[mid] > target:
                r = mid - 1
            elif nums[mid] < target:
                l = mid + 1
        return [res1,res2]


    
