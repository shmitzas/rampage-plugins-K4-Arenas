# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [v1.1.2]

### Changed

- **Config handling refactor**: Migrated to `IOptionsMonitor<PluginConfig>` pattern for hot-reload support and improved config management
  - Config is now accessible via static `Config.CurrentValue` property
  - Uses `IOptionsMonitor` instead of `IOptions` for runtime configuration updates
- **GameRules handling refactor**: Replaced manual GameRules caching with direct `Core.EntitySystem.GetGameRules()` calls
  - Removed `_gameRules` field and `GetGameRules()` helper method
  - GameRules now fetched fresh from entity system when needed
- Aligned config initialization pattern with K4-WeaponPurchase plugin for consistency

### Technical

- Configuration now uses `builder.AddJsonFile(ConfigFileName, optional: false, reloadOnChange: true)` pattern
- Services use `AddOptions<PluginConfig>()` with `IOptionsMonitor` for live configuration updates

## [v1.1.1]

### Fixed

- Fixed `DbPlayer` entity missing `DatabaseGeneratedOption.None` attribute for non-auto-increment primary key

## [v1.1.0]

### Added

- **Multi-database support**: Now supports MySQL/MariaDB, PostgreSQL, and SQLite
- **Database migrations**: Automatic schema management with FluentMigrator
- **ORM integration**: Dapper + Dommel for type-safe database operations
- **Weapon translations**: All weapons now have translatable display names
- **Selected weapon highlighting**: Currently selected weapon is highlighted in menus
- **Improved menus**: Toggle-style round preferences menu with better UX

### Changed

- Refactored database layer to use Dommel ORM instead of raw SQL queries
- Improved database compatibility across different database engines
- Menus now use LinearScroll style and don't freeze the player
- Optimized publish output by excluding unused language resources and database providers

### Fixed

- Fixed SQL syntax compatibility issues with different database engines

## [v1.0.2] - 2025-11-28

### Fixed

- Weapon cache initialization timing issue

## [v1.0.1] - 2025-11-28

### Changed

- Remove unused debug logs

## [v1.0.0] - 2025-11-28

### Added

- Initial Release
