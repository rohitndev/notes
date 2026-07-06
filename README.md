# Python Notes

My working notes on Python — things I keep coming back to.

## Environment Setup

Always use a virtual environment per project:

```bash
python -m venv .venv
.venv\Scripts\activate      # windows
source .venv/bin/activate   # linux / mac
pip install -r requirements.txt
```

Freeze dependencies before sharing:

```bash
pip freeze > requirements.txt
```

## Strings

Prefer f-strings — faster and more readable than `.format()`:

```python
name = "rohit"
print(f"hello {name}, 2 + 2 = {2 + 2}")
```

Useful string methods: `.strip()`, `.split()`, `.join()`, `.startswith()`, `.replace()`.

## Data Structures

```python
# list comprehension beats map/filter for readability
squares = [x * x for x in range(10) if x % 2 == 0]

# dict comprehension
prices = {item: cost * 1.18 for item, cost in cart.items()}

# unpacking
first, *rest = [1, 2, 3, 4]
```

- `list` — ordered, mutable, allows duplicates
- `tuple` — ordered, immutable
- `set` — unordered, unique items, fast membership checks
- `dict` — key/value pairs, insertion ordered since 3.7

## Files

```python
# always use context managers
with open("data.txt", encoding="utf-8") as f:
    for line in f:
        process(line.strip())
```

`pathlib` is nicer than `os.path`:

```python
from pathlib import Path
files = Path("logs").glob("*.log")
```

## Error Handling

```python
try:
    result = risky()
except ValueError as e:
    print(f"bad value: {e}")
finally:
    cleanup()
```

Catch specific exceptions, never bare `except:`.

## Libraries I Use Often

| Library | Purpose |
|---|---|
| `requests` | HTTP calls |
| `pandas` | dataframes / CSV work |
| `fastapi` | REST APIs |
| `pytest` | testing |
| `rich` | pretty terminal output |

## Quick Tips

- `python -m http.server` — instant local file server
- `python -m json.tool file.json` — pretty print JSON
- `if __name__ == "__main__":` guards script entry points
- Use `enumerate()` instead of manual counters
- `zip()` to iterate two lists together

## git

- commit small and often
- `git stash` before switching context
- `git log --oneline -10` for a quick history view
