# Changelog

## 0.5.1 ()

Release 0.5.1 is a minor release and contains new features:
- Added reflexive transitions (thanks to @janLo)
- Wildcards for reflexive (`wildcard_same`) and all (`wildcard_all`) destinations are `Machine` class variables now which can be altered if necessary.

## 0.5.0 (March, 2017)
Release 0.5.0 is a major release:
- CHANGED API: `MachineError` is now limited to internal error and has been replaced by `AttributeError` and `ValueError` where applicable (thanks to @ankostis)
- CHANGED API: Phasing out `add_self`; `model=None` will add NO model starting from next major release; use `model='self'` instead.
- Introduced deprecation warnings for upcoming changes concerning `Machine` keywords `model` and `add_self`
- Introduced `Machine.remove_transition` (thanks to @PaleNeutron)
- Introduced `Machine._create_state` for easier subclassing of states
- `LockedMachine` now supports custom context managers for each model (thanks to @paulbovbel)
- `Machine.before/after_state_change` can now be altered dynamically (thanks to @peendebak)
- `Machine.add_ordered_transitions` now supports `prepare`, `conditons`, `unless`, `before` and `after` (thanks to @aforren1)
- New `prepare_event` and `finalize_event` keywords to handle transitions globally (thanks to @ankostis)
- New `show_auto_transitions` keyword for `GraphMachine.__init__` (default `False`); if enabled, show auto transitions in graph
- New `show_roi` keyword for `GraphMachine._get_graph` (default `False`); if `True`, show only reachable states in retrieved graph
- Test suite now skips contextual tests (e.g. pygraphviz) if dependencies cannot be found (thanks to @ankostis)
- Improved string representation of several classes (thanks to @ankostis)
- Improved `LockedMachine` performance by removing recursive locking
- Improved graph layout for nested graphs
- `transitions.extensions.nesting.AGraph` has been split up into `Graph` and `NestedGraph` for easier maintenance
- Fixed bug related to pickling `RLock` in nesting
- Fixed order of callback execution (thanks to @ankostis)
- Fixed representation of condition names in graphs (thanks to @cemoody)

## 0.4.3 (December, 2016)
Release 0.4.3 is a minor release and contains bug fixes and several new features:
- Support dynamic model addition via `Machine.add_model` (thanks to @paulbovbel)
- Allow user to explicitly pass a lock instance or context manager to LockedMachine (thanks to @paulbovbel)
- Fixed issue related to parsing of HSMs (thanks to @steval and @user2154065 from SO)
- When `State` is passed to `Machine.add_transition`, it will check if the state (and not just the name) is known to the machine

## 0.4.2 (October, 2016)
Release 0.4.2 contains several new features and bugfixes:
- Machines can work with multiple models now (thanks to @gemerden)
- New `initial` keyword for nested states to automatically enter a child
- New `Machine.trigger` method to trigger events by name (thanks to @IwanLD)
- Bug fixes related to remapping in nested (thanks to @imbaczek)
- Log messages in `Transition.execute` and `Machine.__init__` have been reassigned to DEBUG log level (thanks to @ankostis)
- New `Machine.get_triggers` method to return all valid transitions from (a) certain state(s) (thanks to @limdauto and @guilhermecgs)

## 0.4.1 (July, 2016)
Release 0.4.1 is a minor release containing bug fixes, minor API changes, and community feedback:
- `async` is renamed to `queued` since it describes the mechanism better
- HierarchicalStateMachine.is_state now provides `allow_substates` as an optional argument(thanks to @jonathanunderwood)
- Machine can now be used in scenarios where multiple inheritance is required (thanks to @jonathanunderwood)
- Adds support for tox (thanks to @medecau and @aisbaa)
- Bug fixes:
    - Problems with conditions shown multiple times in graphs
    - Bug which omitted transitions with same source and destination in diagrams (thanks to @aisbaa)
    - Conditions passed incorrectly when HSMs are used as a nested state
    - Class nesting issue that prevented pickling with dill
    - Two bugs in HierarchicalStateMachine (thanks to @ajax2leet)
    - Avoided recursion error when naming a transition 'process' (thanks to @dceresuela)


- Minor PEP8 fixes (thanks to @medecau)

## 0.4.0 (April, 2016)
Release 0.4 is a major release that includes several new features:
- New `async` Machine keyword allows queueing of transitions (thanks to @khigia)
- New `name` Machine keyword customizes transitions logger output for easier debugging of multiple running instances
- New `prepare` Transition keyword for callbacks before any 'conditions' are checked (thanks to @TheMysteriousX)
- New `show_conditions` GraphSupport keyword adds condition checks to dot graph edges (thanks to @khigia)
- Nesting now supports custom (unicode) substate separators
- Nesting no longer requires a leaf state (e.g. to_C() does not enter C_1 automatically)
- Factory for convenient extension mixins
- Numerous minor improvements and bug fixes

## 0.3.1 (January 3, 2016)
Mostly a bug fix release. Changes include:
- Fixes graphing bug introduced in 0.3.0 (thanks to @wtgee)
- Fixes bug in dynamic addition of before/after callbacks (though this is a currently undocumented feature)
- Adds coveralls support and badge
- Adds a few tests to achieve near-100% coverage

## 0.3.0 (January 2, 2016)
Release 0.3 includes a number of new features (nesting, multithreading, and graphing) as well as bug fixes and minor improvements:
- Support for nested states (thanks to @aleneum)
- Basic multithreading support for function access (thanks to @aleneum)
- Basic graphing support via graphviz (thanks to @svdgraaf)
- Stylistic edits, minor fixes, and improvements to README
- Expanded and refactored tests
- Minor bug fixes

## 0.2.9 (November 10, 2015)
- Enabled pickling in Python 3.4 (and in < 3.4 with the dill module)
- Added reference to generating Transition in EventData objects
- Fixed minor bugs

## 0.2.8 (August, 6, 2015)
- README improvements, added TOC, and typo fixes
- Condition checks now receive optional data
- Removed invasive basicConfig() call introduced with logging in 0.2.6

## 0.2.7 (July 27, 2015)
- Fixed import bug that prevented dependency installation at setup

## 0.2.6 (July 26, 2015)
- Added rudimentary logging for key transition and state change events
- Added generic before/after callbacks that apply to all state changes
- Ensured string type compatibility across Python 2 and 3

## 0.2.5 (May 4, 2015)
- Added ability to suppress invalid trigger calls
- Shorthand definition of transitions via lists

## 0.2.4 (March 11, 2015)
- Automatic detection of predefined state callbacks
- Fixed bug in automatic transition creation
- Added Changelog

## 0.2.3 (January 14, 2015)
- Added travis-ci support
- Cleaned up and PEP8fied code
- Added 'unless' argument to transitions that mirrors 'conditions'

## 0.2.2 (December 28, 2014)
- Python 2/3 compatibility
- Added automatic to_{state}() methods
- Added ability to easily add ordered transitions
