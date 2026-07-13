<<<<<<< HEAD
# Gen AI Repository Notes

## Git push issue: `rejected] main -> main (fetch first)`

### Problem
When I ran:

```bash
git push -u origin main
```

Git returned:

```bash
! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/santhus3j/Gen_AI.git'
```

### Cause
The remote repository already had a different commit history for `main` than the local repository. Because of that, Git could not do a simple fast-forward push.

### Solution
Run these commands:

```bash
git fetch origin

git pull origin main --allow-unrelated-histories

git add .
git commit -m "Merge remote changes"
git push -u origin main
```

If you want to overwrite the remote branch and you are sure you want to replace it, use:

```bash
git push --force-with-lease origin main
```

> Only use `--force-with-lease` if you understand that it replaces the remote history.

## Common Git checklist

1. Check status:
   ```bash
   git status
   ```
2. Check remotes:
   ```bash
   git remote -v
   ```
3. Fetch remote changes:
   ```bash
   git fetch origin
   ```
4. Merge or rebase:
   ```bash
   git pull origin main
   ```
5. Push again:
   ```bash
   git push -u origin main
   ```

## Notes for future reference

- If Git says `fetch first`, fetch and pull first.
- If Git says `branch has diverged`, use `git pull --allow-unrelated-histories` or inspect the history.
- If Git says `nothing to commit`, the current changes are already saved or there are no new tracked changes.
- Keep this README updated with new problems and solutions.

## GitHub push protection / secret scanning

If GitHub blocks the push with a message such as `GH013` or `Push cannot contain secrets`, do this:

1. Remove the secret from the file content.
2. Commit the cleaned files.
3. If the secret is already present in older commits, rewrite the branch history and push again.

Example:

```bash
git checkout --orphan clean-main
git add -A
git commit -m "Remove secret from history"
git branch -m main
git push --force-with-lease origin main
```

> Use `--force-with-lease` only when you are deliberately replacing the remote branch history.

## Extra note
=======
# Gen_AI
>>>>>>> 83738ae955711ba509348fca322ae1b3ce62519d
Generative AI Daily Updates
