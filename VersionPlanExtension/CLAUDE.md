<!-- CLAUDE CONFIG METADATA -->
<!-- This file was automatically synced from the source repository -->
<!-- Project: VersionPlanExtension -->
<!-- Last Updated: 2025-07-29 -->
<!-- Local Path: /Users/peazeve/GDocs/Projects/VersionPlanExtension -->
<!-- Source Repository: https://github.com/prgazevedo/VersionPlanExtension -->
<!-- End Metadata -->

> **Source Repository**: [VersionPlanExtension](https://github.com/prgazevedo/VersionPlanExtension)  
> **Last Synced**: 2025-07-29  

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview
This is a VSCode extension called "Claude Config Manager" that manages CLAUDE.md files across projects with automatic GitHub repository synchronization. It provides a centralized system for storing and syncing CLAUDE.md configurations using a folder-based repository structure.

## Build Commands
- `npm install` - Install dependencies
- `npm run compile` - Compile TypeScript to JavaScript
- `npm run watch` - Watch for changes and compile automatically
- `npm run lint` - Run ESLint on TypeScript files
- `npm run test` - Run tests (requires compilation first)
- `npm run vscode:prepublish` - Prepare for publishing (runs compile)

## Package and Installation
- `npm install -g vsce` - Install VS Code Extension Manager globally
- `vsce package` - Create .vsix package file
- `code --install-extension claude-config-manager-X.X.X.vsix` - Install from .vsix

## Architecture

### Core Components
1. **Extension Entry Point** (`src/extension.ts`): Main activation logic, command registration, and status bar management
2. **Repository Manager** (`src/repository.ts`): Handles Git operations, cloning, syncing, and auto-commits
3. **File Manager** (`src/fileManager.ts`): Manages CLAUDE.md files, file watching, and sync operations
4. **Template Manager** (`src/templates.ts`): Handles template processing with variable substitution
5. **Token Tracker** (`src/tokenTracker.ts`): Monitors token usage and provides cost estimation and statistics

### Commands Structure
- `src/commands/init.ts` - Initialize repository command
- `src/commands/sync.ts` - Manual sync command
- `src/commands/create.ts` - Create from template command
- `src/commands/edit.ts` - Edit CLAUDE.md command
- `src/commands/usage.ts` - View usage statistics command

### Template System
- Templates in `templates/` directory with variable substitution using `{{variable}}` syntax
- Three built-in templates: basic.md, web-dev.md, data-science.md
- Variables: projectName, description, techStack, author, date

## Key Features
- **Auto-sync**: Watches CLAUDE.md files for changes and automatically syncs to repository
- **Project-based organization**: Each project gets its own folder in the repository (`ProjectName/CLAUDE.md`)
- **Template system**: Create CLAUDE.md files from predefined templates with variable substitution
- **Git integration**: Full Git workflow with pull, commit, and push operations
- **Status bar integration**: Shows sync status and provides quick access to sync command
- **Source repository linking**: Automatically adds metadata linking back to the original project repository
- **Token usage tracking**: Monitors and tracks estimated token usage with cost estimation for each operation
- **Usage statistics**: Comprehensive reporting with daily, weekly, and monthly breakdowns

## Configuration Settings
- `claude-config.repositoryUrl` - GitHub repository URL for configs
- `claude-config.autoSync` - Enable/disable automatic syncing
- `claude-config.autoCommit` - Enable/disable automatic commits
- `claude-config.defaultTemplate` - Default template for new files
- `claude-config.tokenTrackingEnabled` - Enable/disable token usage tracking
- `claude-config.showUsageNotifications` - Show usage notifications after operations

## Development Notes
- Uses `simple-git` library for Git operations
- File watching implemented with VSCode's FileSystemWatcher
- Global storage used for repository location (`context.globalStorageUri`)
- Error handling with status bar updates and user notifications
- Repository structure: `ProjectName/CLAUDE.md` for organization

## Dependencies
- `simple-git` - Git operations
- `fs-extra` - Enhanced file system operations
- `vscode` - VS Code API
- `typescript` - Development dependency
- `eslint` - Code linting

## Recent Bug Fixes (v1.0.0)
- Fixed simple-git initialization error on extension activation
- Removed synchronous git initialization from constructor
- Added lazy-loaded git initialization with proper error handling
- Improved extension activation reliability
- Added better debug logging for troubleshooting

## New Features (v1.1.0)
- **Source Repository Linking**: Automatically detects and adds source repository metadata to synced CLAUDE.md files
- **Metadata Injection**: Adds both hidden HTML comments and visible markdown headers with project information
- **URL Normalization**: Converts SSH URLs to HTTPS for better web compatibility
- **Duplicate Prevention**: Prevents duplicate metadata when re-syncing files

## Version Updates (v3.2.2)
- **Usage Tracking & Statistics**: Added comprehensive token usage tracking with cost estimation
- **Conversation Browser Integration**: Enhanced UI for tracking usage across different conversations
- **Debugging Tools**: Added debugging functionality for testing and troubleshooting
- **Icon Visibility Fix**: Improved extension icon visibility without workspace requirement
- **Publisher ID Compliance**: Updated for VSCode marketplace compliance

## Release Information
- **Current Version**: v3.2.2
- **Package File**: claude-config-manager-3.2.2.vsix
- **Release Date**: July 2025
- **GitHub Repository**: https://github.com/prgazevedo/VersionPlanExtension

# PROJECT_PLAN Integration
# Added by Claude Config Manager Extension

When working on this project, always refer to and maintain the project plan located at `.claude/.plans/PROJECT_PLAN.md`.

**Instructions for Claude Code:**
1. **Read the project plan first** - Always check `.claude/.plans/PROJECT_PLAN.md` when starting work to understand the project context, architecture, and current priorities.
2. **Update the project plan regularly** - When making significant changes, discoveries, or completing major features, update the relevant sections in PROJECT_PLAN.md to keep it current.
3. **Use it for context** - Reference the project plan when making architectural decisions, understanding dependencies, or explaining code to ensure consistency with project goals.

**Plan Mode Integration:**
- **When entering plan mode**: Read the current PROJECT_PLAN.md to understand existing context and priorities
- **During plan mode**: Build upon and refine the existing project plan structure
- **When exiting plan mode**: ALWAYS update PROJECT_PLAN.md with your new plan details, replacing or enhancing the relevant sections (Architecture, TODO, Development Workflow, etc.)
- **Plan persistence**: The PROJECT_PLAN.md serves as the permanent repository for all planning work - plan mode should treat it as the single source of truth

This ensures better code quality and maintains project knowledge continuity across different Claude Code sessions and plan mode iterations.

# important-instruction-reminders
Do what has been asked; nothing more, nothing less.
NEVER create files unless they're absolutely necessary for achieving your goal.
ALWAYS prefer editing an existing file to creating a new one.
NEVER proactively create documentation files (*.md) or README files. Only create documentation files if explicitly requested by the User.