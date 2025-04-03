---
id: query-client
title: QueryClient
sidebar_label: QueryClient
---

## Overview

The `QueryClient` class provides a client interface for interacting with the **Data Services API**. It supports retrieving identities, workflow processes, events, and inventory-related information using HTTP requests.

---

## Initialization

```python
from my_package import QueryClient

client = QueryClient("http://localhost:8105")
```

- **url** (`str` or `callable`): The base URL of the Data Services API.

---

## Context Manager Support

`QueryClient` supports use as a context manager to automatically close the session:

```python
with QueryClient("http://...") as client:
    # Use the client here
    ...
```

---

## HTTP Methods

The following generic HTTP methods are supported:

#### `get(endpoint: str, params: dict = None) -> Response`

Send a `GET` request to the specified endpoint.

### `post(endpoint: str, data: dict = None) -> Response`

Send a `POST` request to the specified endpoint.

### `put(endpoint: str, data: dict = None) -> Response`

Send a `PUT` request to the specified endpoint.

### `delete(endpoint: str) -> Response`

Send a `DELETE` request to the specified endpoint.

---

## API Methods

### `get_identity(item_id: str) -> Identity`

Retrieve a single identity by its ID.

---

### `get_child_identities(parent_type_id: str, limit: int, offset: int) -> List[Identity]`

Retrieve child identities from a given parent.

---

### `remove_identity(item_id: str) -> bool`

Delete an identity by its ID.

---

### `get_workflow_process(workflow_process_id: int) -> WorkflowProcess`

Retrieve a workflow process by ID.

---

### `get_events(search_parameters, limit: int, offset: int) -> List[EventMessage]`

Query for events matching the given search parameters.

---

### `get_items_at_location(location_id: str, limit: int, offset: int) -> List[Identity]`

Return a list of identities at a given location.

---

### `get_items_at_location_async(location_id: str, limit: int, offset: int) -> List[Identity]`

Async version of `get_items_at_location`.

---

### `get_location(item_id: str) -> Location`

Retrieve the location details of a specific item.

---

### `get_materials_in_container(container_id: str) -> List[MaterialInContainerSearchResult]`

Retrieve all materials found inside a container.

---

### `get_materials_in_container_async(container_id: str) -> List[MaterialInContainerSearchResult]`

Async version of `get_materials_in_container`.

---

### `get_net_volume(container_id: str) -> Volume`

Retrieve the net volume of a container.

---

## Notes

- All methods raise HTTP errors if the request fails.
- The `ParameterCollection` used in identity methods is a custom container for `Parameter` objects.
- API responses are converted to Python dataclasses for ease of use.
- For further details, refer to the specific method docstrings in the codebase or the official API specification.

