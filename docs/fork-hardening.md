# Fork hardening: task log privacy

This fork preserves the upstream MIT license and attribution. The first change
removes full task payloads from the two successful task creation/deletion logs.
Task/request identifiers and the creation stage remain available; API responses
and queue behavior are unchanged.

Run the dependency-free regression tests with:

```sh
python -m unittest test.services.test_task_log_privacy -v
```

These tests execute the actual controller function bodies with mocked dependencies
and stripped annotations/decorators. They validate the successful paths only;
they do not validate HTTP integration, providers, or the full application.

This is a narrowly scoped mitigation, not a complete log-redaction policy or
production security approval. Other log sites, identifier handling, access
controls and retention need separate review. No provider, publication or paid
operation is needed for these tests. Bundled media/font/music rights require
separate verification before reuse in a product.

Rollback: revert this change through review. That restores the original payload
logging behavior, so evaluate privacy requirements before doing so.
