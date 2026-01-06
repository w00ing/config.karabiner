# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Karabiner-Elements configuration directory (`~/.config/karabiner/`). Karabiner-Elements is a macOS keyboard customization tool that allows complex key remapping.

## File Structure

- `karabiner.json` - Main configuration file, loaded directly by Karabiner-Elements
- `assets/complex_modifications/*.json` - Reusable rule templates that can be imported into the main config
- `automatic_backups/` - Auto-generated backups (do not edit)

## Configuration Format

The main config uses a JSON structure with:
- `global` - Global settings (e.g., `show_in_menu_bar`)
- `profiles` - Array of profiles, each containing:
  - `complex_modifications.rules` - Array of key remapping rules
  - `simple_modifications` - Direct key-to-key remaps
  - `virtual_hid_keyboard` - Keyboard type settings

### Rule Structure

Each complex modification rule has:
```json
{
  "description": "Human-readable name",
  "enabled": true,  // optional, defaults to true
  "manipulators": [
    {
      "type": "basic",
      "from": { "key_code": "...", "modifiers": {...} },
      "to": [{ "key_code": "..." }],
      "conditions": [...]  // optional app-specific conditions
    }
  ]
}
```

### Key Concepts

- `mandatory` modifiers must be held for the rule to trigger
- `optional` modifiers are passed through to the output
- `frontmost_application_unless` excludes specific apps by bundle ID (regex)
- `to_if_alone` triggers when key is tapped without other keys
- `lazy: true` on modifiers delays registration until another key is pressed

## Current Active Rules

1. Emacs-style Ctrl+P/N for Up/Down arrows
2. Vi-style Ctrl+HJKL for arrow keys (except in iTerm2/Ghostty)
3. Caps Lock as Escape (tap) or Control (hold), also switches to English input
4. Right Command remapped to F19

## Validation

After editing `karabiner.json`, Karabiner-Elements automatically reloads it. Check the Karabiner-Elements GUI or log for parse errors.
