# Unit-5-Searching-and-Algorithm-Analysis
"""
=====================================================
UNIT 5 DISCUSSION: SEARCH ALGORITHMS (LINEAR vs BINARY)
=====================================================

INSTRUCTIONS:
In this assignment, you will implement and analyze two
fundamental search algorithms: linear search and binary search.

You will demonstrate your understanding by modifying the
provided code, running experiments on different dataset sizes,
and clearly explaining your results through code comments
and program output.
"""


def linear_search(lst, target):
    """
    TODO (Student):
    Implement a linear search algorithm.

    Requirements:
    - Search the list from beginning to end.
    - Return the index if the target is found.
    - Return -1 if the target is not found.
    - Add comments explaining why linear search
      has O(n) time complexity.
    """
    # Linear search checks each element one at a time.
    # In the worst case, the target may be at the end
    # of the list or may not exist at all.
    # This means up to n comparisons are required,
    # resulting in O(n) time complexity.
    for index in range(len(lst)):
        if lst[index] == target:
            return index

    return -1


def binary_search(lst, target):
    """
    TODO (Student):
    Implement a binary search algorithm.

    Requirements:
    - Assume the list is already sorted.
    - Repeatedly reduce the search space by half.
    - Return the index if the target is found.
    - Return -1 if the target is not found.
    - Add comments explaining how each iteration
      reduces the search space.
    """
    low = 0
    high = len(lst) - 1

    while low <= high:
        # Locate the middle element
        mid = (low + high) // 2

        if lst[mid] == target:
            return mid

        elif target < lst[mid]:
            # Target is smaller than the middle value.
            # Ignore the right half of the list.
            # This reduces the search space by half.
            high = mid - 1

        else:
            # Target is larger than the middle value.
            # Ignore the left half of the list.
            # This also reduces the search space by half.
            low = mid + 1

    return -1


def main():
    print("=== UNIT 5: SEARCH ALGORITHMS ===")

    # ===============================
    # TODO (Student): SMALL DATASET
    # ===============================
    #
    # Requirements:
    # 1. Create a small sorted dataset.
    # 2. Test both linear search and binary search.
    # 3. Search for:
    #    - a value that exists
    #    - a value that does not exist
    # 4. Use comments to clearly explain the results.

    print("\n=== SMALL DATASET TEST ===")
    small_dataset = [5, 10, 15, 20, 25, 30, 35]
    print("Dataset:", small_dataset)

    # Existing value
    target = 20
    print(f"\nSearching for existing value {target}")
    print("Linear Search Result:", linear_search(small_dataset, target))
    print("Binary Search Result:", binary_search(small_dataset, target))

    # Missing value
    target = 22
    print(f"\nSearching for missing value {target}")
    print("Linear Search Result:", linear_search(small_dataset, target))
    print("Binary Search Result:", binary_search(small_dataset, target))

    # Results:
    # Both algorithms return the correct index when
    # the value exists and return -1 when it does not.
    # With a small dataset, the performance difference
    # between the two algorithms is minimal.

    # ===============================
    # TODO (Student): LARGE DATASET
    # ===============================
    #
    # Requirements:
    # 1. Create a much larger sorted dataset.
    # 2. Test both search algorithms.
    # 3. Compare the results.
    # 4. Use comments to explain why binary search becomes more
    #    efficient as datasets grow larger.

    print("\n=== LARGE DATASET TEST ===")
    large_dataset = list(range(1, 100001))

    target = 99999

    print("Dataset Size:", len(large_dataset))
    print(f"Searching for {target}")

    print("Linear Search Result:",
          linear_search(large_dataset, target))

    print("Binary Search Result:",
          binary_search(large_dataset, target))

    # Comparison:
    # Linear search may need to check nearly every element
    # before finding the target.
    # Binary search repeatedly halves the remaining search
    # area and therefore requires far fewer comparisons.
    # As dataset size increases, binary search becomes much
    # more efficient than linear search.

    # ===============================
    # TODO (Student): EDGE CASES
    # ===============================
    #
    # Demonstrate at least two edge cases.
    #
    # Example ideas:
    # - Empty list
    # - Single-element list
    # - Value not present
    # - Value at the first position
    # - Value at the last position
    #
    # Explain what happens in each case.

    print("\n=== EDGE CASE TESTS ===")
    # Edge Case 1: Empty List
    empty_list = []
    print("\nEmpty List Search")
    print("Linear Search:", linear_search(empty_list, 10))
    print("Binary Search:", binary_search(empty_list, 10))

    # Since the list contains no elements,
    # both algorithms immediately return -1.

    # Edge Case 2: Single Element List
    single_list = [50]
    print("\nSingle Element List Search")
    print("Linear Search:", linear_search(single_list, 50))
    print("Binary Search:", binary_search(single_list, 50))

    # Both algorithms find the target at index 0.

    # Edge Case 3: First Position
    print("\nTarget at First Position")
    print("Linear Search:", linear_search(small_dataset, 5))
    print("Binary Search:", binary_search(small_dataset, 5))

    # Edge Case 4: Last Position
    print("\nTarget at Last Position")
    print("Linear Search:", linear_search(small_dataset, 35))
    print("Binary Search:", binary_search(small_dataset, 35))


if __name__ == "__main__":
    main()
