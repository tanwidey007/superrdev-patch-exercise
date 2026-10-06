# Patch Exercise Notes

## Summary

Fixed three user-facing issues in the task tracker.

1. **Artificial search latency:** Removed the artificial `Thread.sleep()` delay from `TaskController`, which caused short search queries to take significantly longer. Testing showed a reduction from about 928 ms to 21 ms for the query "a".

2. **Loading/error state handling:** Updated `useTasks` so errors clear stale error state and loading is always reset using `finally()`. This prevents the UI from remaining in a loading state after a failed request.

3. **Pagination reset:** Updated `App.jsx` so changing the search query or status filter resets pagination to page 1. This prevents searches or filters from incorrectly starting on an old page.

## What I Did Not Change

I did not modify the database schema, seed data, or repository search query because the existing task loading, search, filtering, and pagination behavior was tested and worked correctly.

## Biggest Remaining Risk

The backend currently retrieves all matching tasks before applying pagination. This may become inefficient with a much larger dataset because pagination is performed in application code rather than directly in the database query.

## Tools / AI Used

Used VS Code, Chrome DevTools, PowerShell, and Git. I used AI assistance to get help in inspecting the code, reason about bugs, suggest focused fixes, and structure the documentation. All implemented changes were manually reviewed and tested.
