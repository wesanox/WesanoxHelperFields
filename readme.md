# Wesanox Helper Fields

A **ProcessWire module** that simplifies the creation and management of fields – directly within modules, templates, or matrix items.  
It is intended for developers who want to dynamically create or remove fields without having to do it manually in the backend.

---

## Features

- Automatic creation of **simple fields** (Text, Textarea, Checkbox, Options, etc.)
- Support for complex field types:
    - **Repeater**
    - **RepeaterMatrix**
    - **CroppableImage3**
    - **Page** and **File**
- Automatic assignment of default values (label, tags, placeholder, icon, column width, etc.)
- Manage and remove unused fields
- Helper methods for:
    - Matrix field types
    - Assigning and cleaning up fields in fieldgroups
    - Automatically adding fields to the corresponding templates

---

The module is configured as **autoload** and is available immediately after installation.

---

## Usage

### 1. Create fields

```php
$modules->get('WesanoxHelperFields')->createFields([
  'name'  => 'my_text_field',
  'label' => 'My Text Field',
  'type'  => 'Text',
  'tags'  => 'custom, helper',
  'placeholder' => 'Enter something...',
]);
```

### 2. Repeater or Matrix fields
More complex fields can also be created easily:

```php
$modules->get('WesanoxHelperFields')->createFields([
    'name'   => 'my_repeater',
    'label'  => 'My Repeater',
    'type'   => 'Repeater',
    'tags'   => 'custom, helper',
    'fields' => ['my_text_field', 'another_field']
]);
```

### 3. Delete fields

```php
$modules->get('WesanoxHelperFields')->deleteFields([
    ['name' => 'my_text_field'],
    ['name' => 'another_field']
]);
```
---
## Methods overview

- createFields(array $field_array)
  Creates a new field based on the given configuration.

- deleteFields(array $fields_array, string $matrix = '', array $matrix_items = [])
  Deletes fields if they are no longer used in fieldgroups. 
- getMatrixKey($matrix): int
  Returns the number of matrix items in a field.

---

## Requirements

- **ProcessWire** ≥ 3.0.210
- **PHP** ≥ 8.0.0