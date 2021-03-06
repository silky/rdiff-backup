RDIFF-BACKUP CHANGELOG
======================

New in v2.0.5 (2020-07-25)
--------------------------

## Changes

* CHG: development status now set to stable in PyPI classifiers
* CHG: increased version of bundled Python Windows version from 3.7.5 
       to 3.7.7. (#426)
* DEV: add measurement of test coverage to tox.ini and limit to 70% for 
       further improvement, closes #113
* DEV: make CI pipeline faster by joining small jobs together to avoid 
       VM creation overhead.
* DOC: add few development notes about profiling rdiff-backup for time 
       and memory consumption

## Authors

* Eric L


New in v2.0.4rc0 (2020-07-12)
-----------------------------

## Changes

* CHG: explicitly refuse to back-up to exFAT because it doesn't handle 
       properly case insensitive deletion of files, closes #38
* CHG: setuptools is a runtime dependency for installation and tests so 
       that version appears correctly instead of DEV, closes #305
* CHG: testing explicitly for existence of tempdir might make certain 
       setups fail now because tempdir was silently ignored
* DEV: Add a misc script to setup an ArchLinux as development platform
* DEV: add a new Vagrant configuration to do some smoke tests between 
       the current/development version and any older one
* DEV: Add samba server with pre-defined shares to Windows vagrant 
       setup to allow for more extensive tests on shares
* DEV: fix compatibility in rollsum and sum-size with rdiff 2.2/2.3 
       leading to errors in librsynctest, closes #304
* DEV: function rpath.getdevnums now also returns the device type, 
       block or char
* DEV: replace deprecated xattr.<verb>xattr with xattr.<verb> function, 
       closes #177
* DOC: added clearer instructions for installing weak dependencies to 
       support ACLs and EAs under CentOS and RHEL
* DOC: fix semi-broken nongnu.org links in manpages of rdiff-backup and 
       rdiff-backup-statistics
* FIX: add python3-setuptools as a run time dependency to Debian 
       package so --version works and doesn't output DEV, closes #305.
* FIX: address `PY_SSIZE_T` deprecation warning appearing under Python 
       3.8 in the C code, closes #374
* FIX: avoid error module 'errno' has no attribute 'EDEADLOCK' under 
       MacOSX, closes #366
* FIX: avoid issue with backslash at the end of file path under 
       Windows, closes #395
* FIX: avoid TypeError: a bytes-like object is required, not 'str' when 
       logging error message by fixing encoding, closes #380
* FIX: explicitly test existence of tempdir and avoid "Can't mix 
       strings and bytes in path components" error, closes #367
* FIX: failed on certain device files with no such file or directory 
       error, closes #401
* FIX: Force encoding of log file to be UTF-8 on all platforms and be 
       lenient to avoid codec errors on logging, closes #356
* FIX: Improve handling of files in use under Windows, closes #392
* FIX: more meaningful error message when trying to test-server a local 
       path, closes #396

## Authors

* Andreas Olsson
* Eric L
* Jirka Vejrazka
* Neha S
* Otto Kekäläinen
* Patrik Dufresne


New in v2.0.3 (2020-05-17)
--------------------------

## Changes

* CHG: multimedia files with extensions ogv, oga, ogm and mkv aren't 
       compressed any more.
* CHG: Rename CHANGELOG to CHANGELOG.md, format to markdown and fix 
       references, closes #279
* FIX: handle properly include/exclude files with Windows/DOS endings, 
       closes #357

## Authors

* Eric L
* Jannis
* Patrik Dufresne

New in v2.0.1rc0 (2020-05-05)
-----------------------------

## Changes

* CHG: return error code 2 instead of number of failed files during 
       repo verification to have a consistent return code (1 would be any 
       other kind of error, or 0 if everything is well), closes #338
* FIX: Added backticks to `<file>` in develop docs so missing word is 
       shown, closes #303
* FIX: allow again to backup from and to Windows shares, closes #337
* FIX: avoid bytes/str object issue under MacOS/X while checking forks 
       FS abilities, closes #320
* FIX: avoid charmap encoding errors during logging on Windows due to 
       extended characters, closes #344
* FIX: avoid IndexError: string index out of range error when using 
       accentuated characters in exclude/include patterns, closes #340
* FIX: avoid test error when using librsync >= 2.2 by adding -R rollsum 
       to rdiff call in librsynctest, closes #304
* FIX: fail with meaningful error message on metadata mirror files with 
       duplicate timestamps, closes #322
* FIX: sequence of exception leading to abort when logging tuple of 
       bytes because of unreachable directory, closes #310
* NEW: Create a new rdiff-backup-delete script which can remove a file 
       and all its history from a backup repository (use with care).
* NEW: option --allow-duplicate-timestamps to only warn about duplicate 
       timestamps in metadata mirror files, use this option with care and only 
       to clean an impacted backup repository.
* DOC: add Fedora and RHEL to installation instructions, and evoke 
       Raspbian, closes #316
* DOC: Update installation steps to make them clearer to users
* DOC: improved installation and contributors documentation
* DEV: clarify version tag pattern and their influence on releases, 
       closes #326
* DEV: much better automated installation of Windows development VM via 
       Vagrant/Ansible
* DEV: errorsrecovertest test script to test recovering from old errors.

## Authors

* albert-github
* dominicraf
* Eric L
* Otto Kekäläinen
* Patrik Dufresne
* Trevor Harmon

New in v2.0.0 (2020-03-15)
--------------------------

## Changes

* FIX: Add workaround to avoid error when backup directory is under the 
       source directory (see issue #296), there is a warning but the backup 
       can succeed.
* FIX: bytestotime() should return None on decode failure (Closes #295)
* NEW: add a unit test for bytestotime() in order to avoid a regression 
       like issue #295.

## Authors

* Eric L
* zjw

New in v1.9.2rc0 (2020-03-08)
-----------------------------

## Changes

* FIX: UpdateError: Updated mirror temp file does not match source, 
       Closes #237
* CHG: Add new logo and improve visual appeal of the README (Closes: 
       #286) (#287)
* NEW: Add Windows developments documentations, closes #220
* FIX: do not fail when starting with uid/gid equal to maximum, avoid 
       OverflowError on os.chown

## Authors

* Eric L
* Patrik Dufresne
* zjw

New in v1.9.1b0 (2020-02-23)
----------------------------

## Changes

* FIX: remove too specific Debian packages from GitHub deployment, 
       closes #263
* NEW: add a new tool to help generate the changelog (description in 
       DEVELOP.md)
* DOC: new release rules and procedure added to docs/DEVELOP.md
* FIX: avoid double unquoting of increment file infos, closes #266
* FIX: versioning of Debian packages follows without glitch the overall 
       tag based versioning.
* DEV: automate via Travis deployment pipeline release to PyPI and Test 
       PyPI.
* FIX: remove some more ugly bytes output in strings using _safe_str, 
       closes #238
* FIX: added and moved hardlinks were not correctly counted and 
       restored, Closes #239
* FIX: rdiff-backup complained about missing SHA checksums of 
       hardlinks, Closes #78
* FIX: avoid int is not iterable error when calling remote command on 
       Windows
* DEV: flake8 checks only setup.py, src, testing and tools code.
* NEW: add support for SOURCE_DATE_EPOCH to override the build date, 
       making reproducible builds possible.
* NEW: sparse files are handled more efficiently, if not compressed and 
       depending on file system

## Authors

* Bernhard M. Wiedemann
* Eric L
* Otto Kekäläinen
* Patrik Dufresne
* Stefan Seyfried
* zjw


New in v1.9.0b0 (2020-01-31)
----------------------------

Different bug fixes, improvements in code and documentation - too many to list
(Andreas Olsson, Andrew Foster, Arrigo Marchiori, bigbear3001, davekempe,
David I. Lehn, elMor3no, Eric Lavarde, Frank Crawford, Jiri Lunacek, joshn, Josh Soref,
mestre, Oliver Lowe, orangenschalen, Otto Kekäläinen, owsla, Patrik Dufresne, Reio Remma,
Rodrigo Silva, Stefan Seyfried, Wes Cilldhaire, zjw)

Add automated of different package formats (Otto Kekäläinen, Arrigo Marchiori, Eric Lavarde)

Add RDIFF_BACKUP_VERBOSITY environment variable (Eric Lavarde)

Add support for Python 3.5 to 3.8, remove support for Python 2.x (Eric Lavarde)

Fix OverflowError on 64-bit systems when backing up symlinks with uid or gid
above INT_MAX. Thanks to Michel Le Cocq for the bug report. (Andrew Ferguson)

Start using Unicode internally for filenames. This fixes Unicode support
on Windows (Josh Nisly)

Don't print "Fatal Error" if --check-destination-dir completed successfully.
Thanks to Serge Zub for the suggestion. (Andrew Ferguson)

Allow --test-server option to be combined with --restrict. Thanks to Nick
Moffitt for reporting the error. Closes Ubuntu bug  #349072. (Andrew Ferguson)


New in v1.3.3 (2009/03/16)
---------------------------

Improve handling of incorrect permissions on backup repository during restore
operation. Closes Ubuntu bug #329722. (Andrew Ferguson)

Don't crash on zlib errors. Closes Debian bug #518531. (Andrew Ferguson)

Make sticky bit warnings quieter while determining file system abilities.
Closes Savannah bug #25788. (Andrew Ferguson)

Fix situation where destination file cannot be opened because of an access
error. Thanks to Dean Cording for the bug report. (Andrew Ferguson)

Fix --compare-hash options on Windows. Thanks to Serge Zub for the fix.


New in v1.3.2 (2009/03/02)
---------------------------

Don't crash when filesystem can't set ACL. Thanks to Matt Thompson for the bug
report. (Andrew Ferguson)

Fix Security Error when performing non-backup operations on Windows. Thanks to
Tommy Keene for the bug report. (Andrew Ferguson)

Properly disable hardlinks by default on Windows.

Fix Python 2.2 compatibility. Closes Savannah bug #25529. (Andrew Ferguson)

Fix typo which caused failure when checking if another rdiff-backup process is
running on Windows. Thanks to Ryan Hughes for the bug report. (Andrew Ferguson)

Disable hardlinks by default on Windows when performing operations such as
--compare, etc. Thanks to Ryan Hughes for the bug report. (Andrew Ferguson)

Change --min-file-size and --max-file-size to agree with man page. These
options no longer include files, and will only apply to regular files. Thanks
to Johannes Jensen for the suggestion. (Andrew Ferguson)

Improve error message if regress operation fails due to Security Violation.
Thanks to Grzegorz Marszalek for the bug report. (Andrew Ferguson)


New in v1.3.1 (2009/01/27)
---------------------------

Improve support for handling too long filenames under Windows. Too long 
directory names and paths are still a problem. (Andrew Ferguson)

Print more helpful error messages when the remote command cannot be started
on Windows. Thanks to Dominic for the bug report. (Andrew Ferguson)

Fix --test-server option when used with remote Windows clients. Thanks to
Thanos Diacakis for testing. (Andrew Ferguson)

Fix --override-chars-to-quote option. (Andrew Ferguson)

Fix typo in robust.py which broke error reporting. Closes Savannah bug #25255.

Ignore Windows errors caused by too long filenames; the files are not yet
backed-up, but the backup process is no longer halted. (Andrew Ferguson)


New in v1.3.0 (2009/01/03)
---------------------------

New option: --use-compatible-timestamps, which causes rdiff-backup to use - as
the hour/minute/second separator instead of :. Enabled by default on systems
which require : to be escaped. (Oliver Mulatz)

Allow rdiff-backup to backup files which it cannot read, but can change
the permissions of. (Andrew Ferguson)

Take start and end times from same system so that the elapsed time printed in
the statistics is not affected by time zone. (Andrew Ferguson)

Properly fix escaping DOS devices and trailing periods and spaces; now supports
native Windows and Linxu/FAT32. (Andrew Ferguson)


New in v1.2.4 (2009/01/01)
---------------------------

Disable escaping trailing spaces and periods for now since it broke remote
restores. Thanks to Dominic for reporting the issue. (Andrew Ferguson)


New in v1.2.3 (2008/12/28)
---------------------------

The official Windows build now includes the librsync patch for files > 4GB.
This requires the Visual C++ 2008 redistributable, available from Microsoft.

The epoch is now a valid date. Closes Savannah bug #24814. (Andrew Ferguson)

Report that connection has dropped if filesystem operation returns ENOTCONN.
Closes Ubuntu bug #219920. (Andrew Ferguson)

Print a more helpful error message if we get an error while reading an old
current_mirror marker. This can happen because it has been locked or deleted
by a just-finished rdiff-backup process. Closes Ubuntu bugs #88140 and
#284506. (Andrew Ferguson)

Do not backup reparse points on native Windows. Thanks to John Covici for
reporting the issue. (Andrew Ferguson)

Support comments in rdiff-backup's ACL files and quote the quoting character
properly if user changed it. (Patch from Oliver Mulatz)

Print a more helpful error message if we cannot read the backup destination.
Closes Ubuntu bug #292586 (again). (Andrew Ferguson)

Print a more helpful error message if we cannot write to the backup
destination. (Andrew Ferguson)

Add ETIMEDOUT to the list of recoverable errors; when irrecoverable, a
ConnectionError is raised. Closes Ubuntu bug #304659. (Andrew Ferguson)

Suppress warnings about the deprecated sha module in Python 2.6. We'll remove
this after rdiff-backup is ported to Python 3. (Patch from Josh Nisly)

Test for symlink permissions now produces a functioning symlink. Thanks to
Julien Poffet for reporting the issue. (Andrew Ferguson)

Fix for crash when deleting read-only files on Windows. (Patch from Josh Nisly)

Fix for Python 2.2 in win_acls.py (Closes Savannah bug #24922).

Throttle verbosity of listattr() warning messages from 3 to 4. (Andrew Ferguson)

Escape trailing spaces and periods on systems which require it, such as
Windows and modern Linux with FAT32. (Andrew Ferguson)

Print nicer error messages in rdiff-backup-statistics (without tracebacks).
Closes Ubuntu bug #292586. (Andrew Ferguson)

Properly handle EINVAL "Invalid argument" errors when setting extended
attributes. Thanks to Kevin Fenzi for reporting the issue. (Andrew Ferguson)

Add warning message if pyxattr is below version 0.2.2. (Andrew Ferguson)

Add "Stale NFS file handle" (ESTALE) to the list of recoverable errors. Thanks
to Guillaume Vachon for reporting the issue. (Andrew Ferguson)

Workaround for broken support for symlink extended attributes in pyxattr < 
0.2.2. Thanks to Leo Bergolth for reporting the issue. (Andrew Ferguson)

Handle ELOOP ("Too many levels of symbolic links") error when reading extended
attributes from symlinks. Closes Savannah bug #24790. (Andrew Ferguson)

Inform the user of which file has failed if an exception occurs during a
rename operation. (Andrew Ferguson)


New in v1.2.2 (2008/10/19)
---------------------------

Automatically resume after a failed initial backup. (Patch from Josh Nisly)

Improve compatibility between Unix and remote native Windows client. It is now
possible to use SSH daemons other than Putty on Windows. (Andrew Ferguson)

Print a more informative error message if the user's remote shell prints
extraneous information before rdiff-backup runs. (Andrew Ferguson)

Don't backup Windows ACLs if the --no-acls option is specified. Thanks to
Richard Metzger for reporting the issue. (Andrew Ferguson)

Add error handling and logging to Windows ACL support; fixes Windows backup to
SMB share. Improve test in fs_abilities to determine if Windows ACLs are
supported. (Andrew Ferguson)

Add a warning message if extended attributes support is broken by the
filesystem (such as with older EncFS versions). (Andrew Ferguson)

Improve handling of Windows ACLs by switching to API functions which
understand inherited ACEs; fixes support for Windows 2000. (Andrew Ferguson)

Support extended attributes on symbolic links. (Andrew Ferguson)

On Mac OS X, read the com.apple.FinderInfo extended attribute since it is the
only storage location for the 'busy' (Z) Finder attribute. (Andrew Ferguson)

Properly fix "AttributeError: RPath instance has no attribute 'inc_compressed'"
bug. Fix in 1.1.12 was in correct place, but wrong solution. (Andrew Ferguson)

Improve support for Python 2.5, which refactored the built-in exceptions so
that SystemExit and KeyboardInterrupt no longer derive from Exception.
Closes support request #106504. (Andrew Ferguson)

Adjust --exclude-if-present option to support directories, symlinks, device
files, etc. Closes bug #24192. Thanks to Vadim Zeitlin for the suggestion.


New in v1.2.1 (2008/08/24)
---------------------------

Produce a new binary for Windows which includes the Python for Windows
Extensions. Thanks to Shohn Trojacek for reporting the problem.

Disable hardlinks by default when backup source or restore destination is
on Windows. (Andrew Ferguson)

Properly catch KeyboardInterrupt on Python 2.5. (Andrew Ferguson)

Don't crash if a CacheIndexable tries to clear a non-existent cache entry,
since the entry must already be cleared. (Andrew Ferguson)


New in v1.2.0 (2008/07/27)
---------------------------

Fall back on the Python make_file_dict function when the filename contains
non-ASCII characters. (Andrew Ferguson)

Ignore Extended Attributes which have Unicode characters outside the current
system representation. These will be correctly handled when rdiff-backup
switches to Python 3, which will have full Unicode support. (Andrew Ferguson)


New in v1.1.17 (2008/07/17)
---------------------------

Move make_file_dict_python so that it is run on the remote end instead of
the local end. This improves performance for Windows hosts since it eliminates
the lag due to checking os.name. It also makes the Windows design parallel
to the Posix design, since the Windows method now returns a dictionary across
the wire. (Andrew Ferguson)

Catch EPERM error when trying to write extended attributes. (Andrew Ferguson)

Allow rdiff-backup to be built into a single executable on Windows using
py2exe ("setup.py py2exe --single-file"). (Patch from Josh Nisly)

Properly handle uid/gid comparison when the metadata about a destination
file has become corrupt. Closes Debian bug #410586. (Andrew Ferguson)

Properly handle hardlink comparison when the metadata about a destination
hardlink has become corrupt. Closes Debian bug #486653. (Andrew Ferguson)

Fix typo in fs_abilities noticed by Martin Krafft. Add EILSEQ ("Invalid or
incomplete multibyte or wide character") to the list of recoverable errors.
Thanks to Hanno Stock for catching that. (Andrew Ferguson)

Catch another reasonable error when reading EAs. (Andrew Ferguson)

Use the Python os.lstat() on Windows. (Patch from Josh Nisly)

Support for Windows ACLs. (Patch from Josh Nisly and Fred Gansevles)

Fix user_group.py to run on native Windows, which lacks grp and pwd Python
modules. (Patch from Fred Gansevles)

Optimize --check-destination and other functions by determining the increment
files server-side instead of client-side. (Patch from Josh Nisly)

Actually make rdiff-backup robust to failure to read an ACL because the file
cannot be found. (Andrew Ferguson)

Get makedist working on Windows. (Patch from Josh Nisly)


New in v1.1.16 (2008/06/17)
---------------------------

Properly preserve hard links when the destination does not support them.
Thanks to Andreas Olsson for noticing the problem. (Andrew Ferguson)

Fix another case where rdiff-backup fails because it has insufficient
permissions on a file it owns. Thanks to Peter Schuller for the test
case. (Andrew Ferguson)

Don't abort if can't read extended attributes or ACL because the path is
considered bad by the EA/ACL subsystem; print a warning instead. Problem
reported by Farkas Levente. (Andrew Ferguson)

rdiff-backup-statistics enhancements suggested by James Marsh: flush stdout
before running other commands, and add a --quiet option to suppress printing
the "Processing statistics from session..." lines. (Andrew Ferguson)

Don't set modification times for directories on Windows. Also, assume
that user has access to all files on Windows since there is no support
for getuid(). (Patch from Josh Nisly)

Add Windows-specific logic for checking if another rdiff-backup process
is running. Do not try to handle non-existant SIGHUP and SIGQUIT signals
on Windows. (Patch from Josh Nisly)

Do not use inode numbers on Windows and gracefully handle attempts to
rename over existing files on Windows. (Patch from Josh Nisly)

Finally fix 'No such file or directory' bug when attempting to regress after
a failed backup. (Patch from Josh Nisly)

Improve Unicode support by escaping Unicode characters in filenames
when printing them in log messages from eas_acls.py. (Fix from
Saptarshi Guha)

Handle Windows' lack of getuid(), getgid(), hardlinks and symlinks in
fs_abilities.py. Use subprocess.Popen() on Windows since it does not support
os.popen2(). (Patch from Josh Nisly)

Let setup.py accept arguments on Windows. (Patch from Josh Nisly)

Get cmodule.c building natively on Windows. (Patch from Josh Nisly)

Don't give up right away if we can't open a file. Try chmod'ing it even
if we aren't root or don't own it, since that can sometimes work on AFS
and NFS. Closes Savannah bug #21202. (Andrew Ferguson)

Correctly handle updates to nested directories with unreadable permissions.
Thanks to John Goerzen for the bug report. Closes Debian bugs #389134 and
#411849. (Andrew Ferguson)

Manpage improvements from Justin Pryzby.

Improve the handling of directories with many small files when backing-up
over a network connection. Thanks to Austin Clements for the test case.
(Andrew Ferguson)

Change high-bit permissions test to check both files and directories.
Improves rdiff-backup's support for AFS and closes Debian bug #450409.
(Patch from Marc Horowitz)

rdiff-backup-statistics now supports quoted repositories. Closes Savannah
bug #21813. (Andrew Ferguson)

Add EBADF to the list of recoverable errors when fsync() is called. This
fixes an rdiff-backup error on AIX and IRIX. Closes Savannah bug #15839.
(Fix from Peter O'Gorman)

Properly initialize new QuotedRPaths. Fixes --list-at-time, etc. when
the target is remote. (Andrew Ferguson)


New in v1.1.15 (2008/01/03)
---------------------------

New feature: If quoting requirements change, rdiff-backup can requote the
entire repository if user specifies the --force option. (Andrew Ferguson)

Don't print the warning message about unsupported hard links if the user
has specified the --no-hard-links option. (Suggested by Andreas Olsson)

Print a more helpful error message when we get a "Result too large"
error when trying to copy a file. (Andrew Ferguson)

Fix bug where rdiff-backup fails after all increments are removed. Closes
Savannah bug #20291. (Andrew Ferguson)

Don't assume that a file cannot be read simply becasue of the access
permissions -- eg, NFS with (rw,all_squash) options. Closes Savannah
bug #21202. (Based on patch from Marc Horowitz)

restore_set_root should check if it can read a particular directory
before checking if "rdiff-backup-data" is contained in it. Closes
Savannah bug #21106. (Patch from Alex Chapman)

Regress.restore_orig_regfile should check if directories can be fsync'd
before doing so. Fixes Savannah bug #21546. (Patch from Marc Horowitz)

Rewrite quoting logic to independently check for escaping Windows special
characters, non-ASCII chars, and uppercase chars. (Andrew Ferguson)

Permit Unicode log messages. (Andrew Ferguson)


New in v1.1.14 (2007/08/13)
---------------------------

New release to work around Python bug. EFTYPE is not defined in Python's
errno module, but is necessary to check on BSD's. (Andrew Ferguson)


New in v1.1.13 (2007/08/12)
---------------------------

Properly pickle QuotedRPaths. Fixes regress operation on quoted filesystems.
Closes Savannah bug #20570 reported by Morgan Read. (Andrew Ferguson)

Warn if can't write extended attribute. (Andrew Ferguson)

Gracefully handle situations where rdiff-backup tries to set the sticky
bit on non-directory files on systems that don't support that action.
Thanks to Jim Nasby for the bug report. (Andrew Ferguson)

Prevent the extended filenames / UTF-8 test from raising an exception
on broken CIFS configurations which transform some characters to '?'.
Problem reported by Luca Cappe. (Andrew Ferguson)

Cygwin on FAT32 hangs when trying to open a file named "aux". Change
the escape DOS devices test to use "con" instead. (Andrew Ferguson)

Fix symlink behavior when filesystem is mounted via CIFS. Closes
Savannah bug #20342. (Andrew Ferguson)

Fix "too many open files" bug when handling large directories. Patch
from Anonymous in Savannah bug #20528.

New options: --tempdir and --remote-tempdir. The first one sets the
directory that rdiff-backup uses for temporary files on the local system.
The second adds the --tempdir option with the given path when invoking
rdiff-backup on remote systems. (Andrew Ferguson)

Don't run the extended attributes test if rdiff-backup is run with
the --no-eas option. Prevents hang in isolated cases. (Andrew Ferguson)

Don't throw an error when clearing extended attributes if they are not
supported on the file. (Andrew Ferguson)


New in v1.1.12 (2007/07/12)
---------------------------

Use .dll as library file extension on Cygwin and Windows. (Andrew Ferguson)

Avoid setting permissions to 000 because they're out of sync. (Andrew Ferguson)

listxattr() can also throw EPERM error if not supported. (Andrew Ferguson)

Do something sensible if we get an IOError while trying to appropriately
log another exception. (Andrew Ferguson)

Handle exception when get permission denied on a file while trying
to establish case sensitivity on read-only side. (Andrew Ferguson)

Finally solve AttributeError due to no 'inc_compressed' attribute
that occured during some regress operations. (Andrew Ferguson)

Squash bug where --check-destination-dir or regress operation failed
after crash when --force option was not used. RPath's are now
properly pickled. (Andrew Ferguson)

Workaround for tempfile.TemporaryFile() having different behavior
on Windows/Cygwin. (Andrew Ferguson)

Make --check-destination-dir handle quoted situations. (Andrew Ferguson)

Handle quoted current_mirror markers and clean-up the listing of
increments with quoted names. (Andrew Ferguson)

Warn if file modification time is before 1970. (Andrew Ferguson)


New in v1.1.11 (2007/06/15)
---------------------------

Fix typo in Main.py introduced in 1.1.9 (Andrew Ferguson)

FIFOs don't have extended attributes -- don't try to access them.
(Andrew Ferguson)

Fix for bug #19612 -- Incorrect line broke --no-compression option.
(Fix by Thiago in bug comment)

Fix for bug #19896 -- symlink() doesn't work on a CIFS-mounted Windows
share.  (Jonathan Hankins)

Fix for bug #19895 -- eliminate traceback for special file detection
on CIFS mounts.  (Jonathan Hankins)


New in v1.1.10 (2007/05/12)
---------------------------

New --exclude-if-present option (i.e. --exclude-if-present .nobackup).
(Jeff Strunk).

Use signal 0 rather than signal.NSIG when testing if another rdiff-backup
is still running.  (Patch from Sébastien Maret)

Sockets don't have extended attributes -- don't try to access them.
(Patch from Andrew Ferguson.)

Fix restore from read-only bug -- rx perms on a repository directory are
enough, no need for write perms when restoring.  (patch from Andrew Price)

Fix --list-increments bug in set_must_escape_dos_devices.
(Marc Dyksterhouse)


New in v1.1.9 (2007/01/29)
--------------------------

Cygwin generates OSError when changing permissions on partitions.
(Patch from Andrew Ferguson.)

Fix fs_abilities.py patch error with set_escape_dos_devices.
(Marc Dyksterhouse)

Glob escaping support via backslash.  (Andrew Price)


New in v1.1.8 (2007/01/29)
--------------------------

Cygwin generates EACCESS on fsync -- so accept it rather than dieing.
(Marc Dyksterhouse).

Add "FilenameMapping.set_init_quote_vals" security exception.
(Marc Dyksterhouse)

Escape DOS device filenames when necessary.  Adjust DOS filename
quoting to work properly with cygwin.  (Marc Dyksterhouse)

Allow for preservation of FinderInfo for folders and fix typo
in Time.py. (Patch from Andrew Ferguson.)

Test for symlink permissions support to avoid unnecessary syscalls on
platforms that don't support them. (Patch from Andrew Ferguson.)

RPM specfile update from Gordon Rowell.


New in v1.1.7 (2006/11/12)
--------------------------

Fix showstopper problem on OSX handling pre-1.1.6 rdiff-backup metadata.
(Patch from Andrew Ferguson.)


New in v1.1.6 (2006/11/11)
--------------------------

Man page update from roland <devzero@web.de>.

--min-file-size/--max-file-size support.  (Patch from Wout Mertens.)

Mac OS X Extended Attributes support.  (Patch from Andrew Ferguson.)

Preserve Mac OS X 'Creation Date' field across backups.  (Patch from Andrew
Ferguson.)

Set symlink permissions properly.  (Patch from Andrew Ferguson.)

Selection fix: empty directories could sometimes be improperly
excluded if certain include expressions involving a non-trailing '**'
were used.  Bug reported by Toni Price.

A few minor changes to help rdiff-backup back up to an SMB/CIFS share.
Thanks to Cengiz Gunay for testing.

Fix a traceback due to an off-by-1 error in "--remove-older-than nB".

Fix a security violation when restoring from a remote repository.
(Patch from Charles Duffy.)

Added times like "Mon Jun 5 11:00:23 1997" to the recognized time
strings.  (Suggested by Wolfgang Dautermann.)


New in v1.1.5 (2006/01/01)
--------------------------

rdiff-backup will now exit by default if it thinks another
rdiff-backup process is currently working on the same repository.

Empty error_log, mirror_metadata, extended_attribute, and
access_control_lists files will no longer be gzipped (suggestion by
Hans F. Nordhaug).

Fix for restoring files in directories with really long names.

Added supplementary rdiff-backup-statistics utility for parsing
rdiff-backup's statistics files (originally based off perl script by
Dean Gaudet).

rdiff-backup should now use much less memory than v1.1.1-1.1.4 if you
have lots of hard links.


New in v1.1.4 (2005/12/13)
--------------------------

Quoting should be enabled only as needed between case-sensitive and
non-case-sensitive systems (thanks for Andrew Ferguson for report).

Files with ACLs will not be unnecessarily marked as changed (bug
report by Carsten Lorenz).

Fix for common KeyError bug introduced in v1.1.3.


New in v1.1.3 (2005/11/25)
--------------------------

Regression metadata bug introduced with 1.1.1/1.1.2 fixed.

rdiff-backup should now give a clean error message (no stack traces!)
when aborted with control-C, killed with a signal, or when the
connection is lost.

When removing older than, delete empty increments directories

Long filename bug finally fixed (phew).  rdiff-backup should now
correctly mirror any file that it can read.

Due to very detailed error report from Yoav, fixed a "Directory not
empty" error that can arise on emulated filesystems like NFS and
EncFS.

Cleaned up remove older than report, and also stopped it from deleting
current data files if you specify a time later than the current
mirror.


New in v1.1.2 (2005/11/06)
--------------------------

This version corrects a packaging error in v1.1.1, which was totally
broken.


New in v1.1.1 (2005/11/05)
--------------------------

rdiff-backup now writes SHA1 sums into its mirror_metadata file for
all regular files, and checks them when restoring.

The above greatly increases the size of the mirror_metadata files, so
diff them for space efficiency, as suggested by Dean Gaudet.

Added two new comparison modes: full file (using the --compare-full or
--compare-full-at-time) or by hash (--compare-hash and
--compare-hash-at-time).

Applied Alec Berryman's patch to update the no-compression regexp.

Alec Berryman's fs_abilities patch is supposed to help with AFS.

Fixed filename-too-long crash when quoting.

Patched carbonfile support, re-enabled it by default.


New in v1.1.0 (2005/10/24)
--------------------------

Refactored fs_abilities for more flexibility.  In particular, avoid
quoting if both source and destination file systems are
case-insensitive.

Increased buffer sizes by factor of 4, because everyone probably has 4
times as much RAM now as when I originally picked those values.

When possible, fsync using a writable file descriptor.  This may help
with cygwin.  (Requested/tested by Dave Kempe.)

Support req 104755: Added --preserve-numerical-ids option, which makes
rdiff-backup preserve uids/gids instead of unames/gnames.  (Suggested
by Wiebe Cazemier)

Fix for bug #14799 reported by Bob McKay:  Crash when backing up files
with high permissions (like suid) to some FAT systems.


New in v1.0.2 (2005/10/24)
--------------------------

Fix for spurious security violation from --create-full-path (reported
by Mike Bydalek).

Fix for bug 14545 which was introduced in version 1.0.1:  Quoting
caused a spurious security violation.  (Important for Mac OS X)

An error reading carbonfile data on Mac OS X should no longer cause a
crash.  (Thanks to Kevin Horton for testing.)

Carbonfile support now defaults to off, even if the system appears to
support it.  It can be manually enabled with the --carbonfile switch.
If you know something about Mac OS X and want to look at the
carbonfile code so it can be re-enabled by default, please do so :)
(help available from list)


New in v1.0.1 (2005/09/10)
--------------------------

Fix for "'filetype' of type exceptions.KeyError" error when restoring.
Test case provided by Davy Durham.  (The problem was the
mirror_metadata file could become un-synced when a file is deleted
when rdiff-backup is running and later the directory that file is in
gets deleted.)

Librsync signature blocksize now based on square root of file length.

rdiff-backup now writes its PID to current_mirror marker (suggested by
Kevin Spicer).

fsync_directories defaults to None, to avoid errors in testing
(suggestion by Charles Duffy).

bug#14209: Security bug with --restrict-read-only and
--restrict-update-only allowed file statting and directory listing
outside path.  Bug with --restrict option allowed writes outside path.
(Reported by Charles Duffy.)

bug #14304: Python 2.2 compatibility spoiled by device files.

lchown no longer required, which is good news for Mac OS X 10.3.


New in v1.0.0 (2005/08/14)
--------------------------

Handle cases of junk uid/gids better on 64bit systems.  (Bug report by
Nick Bailey)

Filenames in the file_statistics*gz files are now quoted the same way
as filenames in the metadata file (LF => \n and \ => \\).

Fix from Paul P Komkoff Jr for uid typo in text_to_entrytuple.

bug#12726: fix regressing of devices while running as non-root -- zero
length files are created as placeholders.

bug#13476: must always compare device numbers when we compare inode
numbers -- fix a non-fatal problem with hardlinks when a filesystem is
moved to another device (and the inodes don't change).

bug#13475: correct an UpdateError when backing up hardlinks with EAs
and/or ACLs.

debian bug#306798: SELinux security attributes can not be removed and
rdiff-backup should not fail when it fails to remove them from temp
files.  fix from Konrad Podloucky.

bug#12949: eliminate an exception during fs abilities testing on OS X 10.4.
fix from Daniel Westermann-Clark.

patch#4136: OSX filename/rsrc has been deprecated for some time, and as of OSX
10.4 it causes log spam.  the new proper use is filename/..namedfork/rsrc.  fix
from Daniel Westermann-Clark.

Log EACCES from listxattr rather than raising an exception -- this can happen
when the repository has permission problems.

Added Keith Edmunds patch adding the --create-full-path option.

Fixed selection bug reported by Daniel Richard G.

bug#13576: You can now back ACLs to a computer that doesn't have the
posix1e module.

bug#13613: Fix for overflow error that could happen when backing up
files with dates far in the future on a 64bit machine to a 32 bit one.

Symlink ownership should be preserved now.  Reported by Naoki
Takebayashi and others.


New in v0.13.6 (2005/04/07)
---------------------------

Fixed timezone bug.  Hopefully this is the last one.  (Thanks to
Randall Nortman for bug report.)

Added fix for listing/restoring certain bad archives made when there
was a timezone bug.  (Thanks to Stephen Isard)

************** Serious bug fix ******************
If a directory in the source directory was replaced by certain
symlinks, then if later backups failed they could cause files in the
directory that the symlink pointed to to be deleted!  Much thanks to
Alistair Popple for pointing this bug out and providing a test case.


New in v0.13.5 (2005/03/28)
---------------------------

Added error-correcting fsync suggestion by Antoine Perdaens.
rdiff-backup may work better with NFS now.

Fix by Dean Gaudet for --calculate-average mode (it broke somewhere in
0.13.x).

Fix for regress warning code:  rdiff-backup should warn you if you are
trying to back up a directory into itself.

Fix for restoring certain directories when not run as root.

Now when determining group permissions check supplementary groups as
well as main group.  (Bug report by Ryan Castle.)

Fixed bug which could cause crash when backing up 3 or more hard
linked files and the first gets deleted during processing.  (Thanks to
Dean Gaudet for bug report.)

Fixed user/group restoring error noticed by Fran Firman.

Checked in Robert Shaw's --chars-to-quote patch

Treated hard link permission problem on Mac OS X by applying
suggestion by David Vasilevsky

Dean Gaudet's patch fixes "--restrict /" option.

Added Robert Shaw's --exclude-fifo, --include-symbolic-links,
etc. options.

Added Maximilian Mehnert's fix for too many open files bug.


New in v0.13.4 (2004/01/31)
---------------------------

Checked in patch by John Goerzen to support Mac OS X Finder
information.  As John says:
> Specifically, it adds storage of:
> 
>  * 4-byte creator
>  * 4-byte type
>  * integer flags
>  * dual integer location
Much thanks to John for adding this useful feature all by himself!

Added --compare and --compare-at-time switches for comparing a
directory with the backup information saved about it.  Thanks to Erik
Forsberg, who noticed that this feature was missing.

Regressing and restoring should now take less memory when processing
large directories (noticed by Luke Mewburn and others).

When regressing, remove mirror_metadata and similar increments first.
This will hopefully help regressing a backup that failed because disk
was full (reported by Erik Forsberg).

Fixed remote quoting errors found by Daniel Drucker.

Fixed handling of (lack of) daylight savings time.  Earlier bug would
cause some files to be marked an hour later.  Thanks to Troels Arvin
and Farkas Levente for bug report.

Altered file selection when restoring so excluded files will not be
deleted from the target dir.  The old behavior was technically
intended and documented but not very convenient.  Thanks to Oliver
Kaltenecker for bug report.

Fixed error when --restrict path given with trailing backslash.  Bug
report by Åke Brännström.

Fixed many functions like --list-increments, --remove-older-than,
etc. which previously didn't work with filename quoting.  Thanks to
Vinod Kurup for detailed bug report.


New in v0.13.3 (2003/10/14)
---------------------------

Fixed some of the --restrict options which would cause spurious
violation errors.

--list-changed-since and --list-at-time now work remotely.
Thanks to Morten Werner Olsen for bug report.

Fixed logic bug that could make restoring extremely slow and waste
memory.  Thanks for Jacques Botha for report.

Fixed bug restoring some directories when mirror_metadata file was
missing (as when made by 0.10.x version).

Regressing and restoring as non-root user now works on directories
that contain unreadable files and directories as long as they are
owned by that user.  Bug report by Arkadiusz Miskiewicz.  Hopefully
this is the last of the unreadable file bugs...

Rewrote hard link tracking system.  New way should use less memory.

Fixed bug causing rdiff-backup to crash when backing up from system
supporting EAs/ACLs to one that didn't.


New in v0.13.2 (2003/09/16)
---------------------------

Change ownership policy and added --user-mapping-file and
--group-mapping-file switches.  See man page for more information.

Added option --never-drop-acls to cause fatal error instead of
dropping any acls or acl entries.  Thanks to Greg Freemyer for
suggestion.

Specified socket type as SOCK_STREAM.  (Error reported by Erik
Forsberg.)

Fixed bug backing up unreadable regular files and directories when
rdiff-backup is run by root on the source site and non-root on the
destination side.  (Reported by Troels Arvin and Arkadiusz
Miskiewicz.)

If there is data missing from the destination dir (for instance if a
user mistakenly deletes it), only warn when restoring, instead of
exiting with error.

Fixed bug in EA/ACL restoring, noticed by Greg Freemyer.

Updated quoting of filenames and extended attributes names to match
forthcoming attr/facl utilities.  Strange characters should now be
properly escaped.

Fixed problems with --restrict options that would cause proper
sessions to fail.  Thanks to Randall Nortman for error report.

Added new time specification by backup number.  So now you can
'--remove-older-than 2B' or '--list-at-time 0B'.  Original suggestion
by Alan Bailward.

File examples.html added to distribution; examples section removed
from man page.

Removed option --no-change-dir-inc-perms.  Instead when copying
permissions to directory increments, mask with 0777.


New in v0.13.1 (2003/08/08)
---------------------------

Restore of archives made by 0.10.x and earlier fixed, although hard
link information is not restored unless it is current in the mirror.
(Bug reported by Jeff Lessem.)

Fixed problem with door files locally when repository is remote.
(Reported by Robert Weber.)

Patch by Jeffrey Marshall fixes socket/fifo recognition on Mac OS X
(which apparently has buggy macros).

Patch by Jeffrey Marshall fixes --calculate-average mode, which seems
to have broken recently.

rdiff-backup should now work and build with python 2.3.  Thanks to
Arkadiusz Miskiewicz and Arkadiusz Patyk for bug reports and a patch.

rdiff-backup now builds and requires librsync 0.9.6.  This version
should be much better than the old one and everyone should probably
upgrade.  Much thanks to Donovan Baarda for all the work that went
into this release.


New in v0.13.0 (2003/07/22)
---------------------------

To prevent the buildup of confusing and error-prone options, the
capabilities of the source and destination file systems are now
autodetected.  Detected features include allowed characters, extended
attributes, access control lists, hard links, ownership, and directory
fsyncing.  Options such as --windows-mode, --chars-to-quote,
--quoting-char, and --windows-restore-mode have been removed.

Now rdiff-backup supports user extended attributes (EAs).  To take
advantage of this you will need the python module pyxattr and a file
system that supports EAs.  Thanks to Greg Freemyer for valuable
discussion.

Support for access control lists (ACLs) was also added.  An ACL
capable file system and the python package pylibacl (which exports the
posix1e module) are required.  Thanks to Greg Freemyer for valuable
discussion.

Thanks to patches by Daniel Hazelbaker, rdiff-backup now reads and
writes Mac OS X style resource forks!

****** Warning ****** The above features are new to this development
release, and it is difficult to test all the possibly combinations of
source and destination file systems.  They should not be considered
stable.  However, help would be appreciated testing these new
features.

****** Warning #2 ****** rdiff-backup records ACL and EA information
in files designed to be compatible with the utilities "getfacl" and
"getfattr".  However, there is a possible security hole in both these
formats (see
http://acl.bestbits.at/pipermail/acl-devel/2003-June/001498.html).
rdiff-backup's format will be fixed when getf{attr|acl}'s is.

Added --list-increment-sizes switch, which tells you how much space
the various backup files take up.  (Suggested by Andrew Bressen)

Although it should be detected automatically, can avoid copying
permissions to directory increments with --no-change-dir-inc-perms.
(Problem on FreeBSD when backing up sticky directories reported by
Troels Arvin.)

Fixed bug with --check-destination and --windows-mode reported by
Tucker Sylvestro.

The librsync blocksize is now chosen based on filesize.  This should
make operations on large files faster (in some cases, orders of
magnitude faster).  Thanks to Ty! Boyack for bringing this issue to my
attention.


New in v0.12.0 (2003/06/26)
---------------------------

Fixed (?) bug that caused crash when file changes type from regular
file in middle of download (reported by Ty! Boyack).

Failure to construct regular file in regression/restoration only
causes warning, not fatal error.

Removed --exclude-mirror option.  (Probably no one uses this, and it
adds clutter.)

--include and --exclude options should work now with restores, with
some speed penalty.


New in v0.11.5 (2003/06/20)
---------------------------

Added EDEADLOCK to the list of skippable errors.  (Thanks to Dave
Kempe for report.)

Added --list-at-time option at request of Farkas Levente.

Various fixes for backing up onto windows directories.  Thanks to
Keith Edmunds for bug reports and testing.

Fixed possible crash when a file would be deleted while being
processed (reported by Robert Weber).

Handle better cases when there are two files with the same name in the
same directory.

Added --windows-restore switch, for use when when restoring from a
windows-style file system to a normal one.  Use --windows-mode when
backing up.

Scott Bender's patch fixes backing up hard links when first linked
file is quoted.


New in v0.11.4 (2003/03/15)
---------------------------

Fixed bug incrementing sockets whose filenames were pretty long, but
not super long.  Reported by Olivier Mueller.

Added Albert Chin-A-Young's patch to add a few options to the setup.py
install script.

Apparently fixed rare utime type bug.  Thanks to Christian Skarby for
report and testing.

Added detailed file_statistics (in addition to session_statistics) as
requested by Dean Gaudet.  Disable with --no-file-statistics option.

Minor speed enhancements.


New in v0.11.3 (2003/03/04)
---------------------------

Fixed a number of bugs reported by Olivier Mueller:

	Brought some old parts of the man page up-to-date.

	Fixed bug if unrecoverable error on second backup to a directory.

	Fixed spurious error message that could appear after a successful
	backup.

	--print-statistics option works again (before it would silently
	ignored).

	Fixed cache pipeline overflow bug.  This error could appear on
	large remote backups when many files have not changed.


New in v0.11.2 (2003/03/01)
---------------------------

Fixed seg fault bug reported by a couple sparc/openbsd users.  Thanks
to Dave Steinberg for giving me an account on his system for testing.

Re-enabled --windows-mode and filename quoting.

Fixed selection bug:  In 0.11.1, files which were included in one
backup would be automatically included in the next.  Now you can
include/exclude files session-by-session.

Fixed ownership compare bug:  In 0.11.1, backups where the destination
side was not root would preserve ownership information by recording it
in the metadata file.  However, mere ownership changes would not
trigger creation of new increments.  This has been fixed.

Added the --no-inode-compare switch.  You probably don't need to use
it though.

If a special file cannot be created on the destination side, a 0
length regular file will be written instead as a placeholder.
(Restores should work fine because of the metadata file.)

Yet another error handling strategy (hopefully this is the last one
for a while, because this stuff isn't very exciting, and takes a long
time to write):

	All recoverable errors are classified into one of three groups:
	ListErrors, UpdateErrors, and SpecialFileErrors.  rdiff-backup's
	reaction to each error is more formally defined (see the error
	policy page, currently at
	http://rdiff-backup.stanford.edu/error_policy.html).

	rdiff-backup makes no attempt to recover or clean up after
	unrecoverable errors.

	However, it now uses fsync() to increment the destination
	directory in a reversable way.  If there is an error, the next
	backup will regress the destination directory into its state
	before the aborted backup.

	The above process can be done without a backup with the
	--check-destination-dir option.

Improved error logging.  Instead of the old haphazard reporting
method, which sometimes didn't indicate the file an error occurred on,
now all recoverable errors are reported in a standard format and also
written to the error_log.<time>.data file in the rdiff-backup-data
directory.  Thanks to Dean Gaudet and others for repeatedly bugging me
about this.


New in v0.11.1 (2002/12/31)
---------------------------

**Warning** Various features have been removed from this version, so
this is not a safe upgrade.  Also this version has less error
checking, and, if it crashes, this version may be more prone to leave
the destination directory in an inconsistent state.  I plan to look at
these issues in the next version.  Also, this version is quite
different from previous ones, so you cannot run version 0.11.1 on one
end of a connection and any previous version on the other side.

The following features have been removed:

	--mirror-only option:  If you just want to mirror something, use
	rsync.  (Or you could use rdiff-backup and then just delete the
	rdiff-backup-data directory, and then update the root mtime.)

	--change-source-perms option:  This feature was pretty complicated
	to implement, and if something happened to rdiff-backup during a
	transfer, the old permissions could not be restored.

	All "resume" related functionality, like --checkpoint-interval:
	This was complicated to implement, and didn't seem to work all
	that well.

	Directory statistics file:  Although the session statistics file is
	still generated, the directory statistics file no longer is,
	because the new code structure makes it less inconvenient.

	The various --exclude and --include options no longer work when
	restoring.  This may be added later if there is demand.

	--windows-mode and filename quoting doesn't work.  There have been
	several requests for this in the past, so it will probably be
	re-added in the next version.

Extensive refactoring.  A lot of rdiff-backup's code was structured as
if it were still in one file, so it didn't make enough use of Python's
module system.

Now rdiff-backup writes metadata (uid, gid, mtime, etc.) to a
compressed text file in the rdiff-backup-data directory.  Here are
some ramifications:

	A user does not need root access on the destination side to record
	file ownership information.

	Some files may be recognized as not having changed based on this
	metadata, so it may not be necessary to traverse the whole mirror
	directory.  This can reduce file access on the destination side.

	Even when the --no-hard-links option is given when backing up,
	link relationships can be restored properly.  However, if this
	option is given, mirror files will not be linked together.

	Special file types like device and sockets which cannot be created
	on the remote side for some reason can still be backed up and
	restored properly.

Fixed bug with the --{include|exclude}-globbing-filelist options
(reported by Claus Herwig).

Added --list-changed-since option to list the files changed since the
given date, and added Bud Bruegger's patch to that.  The format and
information this option provides will probably change in the near
future.

Restoring is now pipelined for better high latency performance, and
unchanged files in the target directory will not be recopied.


New in v0.11.0 (2002/10/05)
---------------------------

If get a socket error from trying to create a socket whose name is too
long, just skip file instead of exiting with error (bug report by Ivo
De Decker).

Added --exclude-special-files switch, which excludes fifos, symlinks,
sockets, and device files.

--windows-mode is now short for --windows-time-format --chars-to-quote
A-Z: --no-hard-links --exclude-special-files.  Thanks to Paul-Erik
Törrönen for some helpful windows info.

Multiple --include and --exclude statements can now be given in a
single file.  See the documentation on
--{include|exclude}-globbing-filelist.  Thanks to Henrik Lewander for
pointing out that command line length could otherwise be a problem.

Fixed bug in filelist processing that ignored leading or trailing
whitespace in filelists.  Now filenames with, for instance, trailing
spaces can be used in filelists.  Filelists which took advantage of
this bug for formatting may have to be edited.

Applied major/minor patch contributed by David S.  rdiff-backup should
now correctly copy device files on platforms such as NetBSD.

It is now possible to restore from a read-only filesystem (before
rdiff-backup would fail when trying to open log file).  Thanks to
Gregor Zattler for bug report.

Fixed bug that prevented certain restores when the source directory
was specified with a trailing backslash.

Added a bit more logging so it should be apparent which file was being
processed when an error occurs (thanks to Gerd Knops for suggestion).

Fixed bug when using --chars-to-quote and directory deleted that has
quoted characters in it.


New in v0.10.1 (2002/09/16)
---------------------------

rdiff-backup should now correctly handle files larger than 2GB.
Thanks to Russ Allbery for telling me how to do this.


New in v0.10.0 (2002/09/10)
---------------------------

Fixed bug, probably introduced in 0.9.3, which prevented restores from
a local source to a remote destination.  Reported by Phillip Eby.

Fixed another bug reported by Phillip Eby, where restores would fail
if rdiff-backup had only been run once and no increments were
available.

A few man page additions regarding restoring, statistics, and
--test-server (thanks to Gregor Zattler, Christopher Schanzle, and
Tobias Polzin for suggestions).

Fixed comparison bug where rdiff-backup would unnecessarily report a
directory as changed when its source size differed from its mirror
size.  Thanks to Tim Allen for report.


New in v0.9.5 (2002/08/09)
--------------------------

Fixed --verbosity option (now both -v and --verbosity work).  Thanks
to Chris Dumont for report.

****** IMPORTANT ****** Fixed serious permissions bug found by Robert
Weber.  Previous versions in the 0.9.x branch would throw away high
bit permissions (like the setuid and setuid bits).  This would be
especially bad when running with the --change-source-perms operation.
Anyone running 0.9.0 - 0.9.4 should upgrade immediately.

Complain about --change-source-perms when running as root, as this
option should not be necessary then.

Fixed bug with --windows-mode.  Thanks to Chris Grindstaff for report.


New in v0.9.4 (2002/07/24)
--------------------------

Man page now correctly included in rpm.

To prevent confusion, rdiff-backup script does not have exec
permissions until it is installed (thanks Jason Piterak).

Sockets are now replicated.  Why not?  (Suggestion by Mickey Everts)

Bad resuming information (because, say, it is left over from a
previous version) should no longer cause exit, except when --resume is
specified.

Better error handling in certain cases when errors occur in file reads
(thanks to John Goerzen for report).


New in v0.9.3 (2002/07/15)
--------------------------

Added --sleep-ratio option after hearing that rdiff-backup was too
hard on hard disks (thanks to Steve Alexander for the suggestion).
Quick example:  --sleep-ratio 0.25 makes rdiff-backup sleep about 25%
of the time.  Maybe this will help on bandwidth usage also.

Fixed -m/--mirror-only option.

Added --exclude-other-filesystems option.  Thanks to Paul Wouters for
the suggestion.

Added convenience field TotalDestinationSizeChange (total change in
destination directory - mirror change + increments change) to
session_statistics file.

Handle a particular situation better where a file changes in a certain
way while rdiff-backup is processing it.  Before rdiff-backup would
just crash; now it skips the file.  Thanks to Scott Bender for the bug
report.

A couple interface fixes to --remove-older-than.

Added some security features to the protocol, so rdiff-backup will now
only allow commands from remote connections.  The extra security will
be enabled automatically on the client (it knows what to expect), but
the extra switches --restrict, --restrict-update-only, and
--restrict-read-only have been added for use with --server.


New in v0.9.2 (2002/06/27)
--------------------------

Interface directly with librsync(.a|.so) instead of running "rdiff"
command line utility.  This can significant save fork()ing time when
processing lots of smallish files that have changed.  Also, rdiff is
no longer required to be in the PATH.

Further speed optimizations, mostly reducing CPU consumption when
scanning through unchanged files.

Fixed Path bug which could caused globbing and regexp include/exclude
statements to malfunction when the base of the source directory was
"/" (root of filesystem).  Thanks to Vlastimil Adamovsky for noting
this bug.

Added quoting for spaces in directory_statistics file, hopefully
making it easier to parse.


New in v0.9.1 (2002/06/19)
--------------------------

Fixed some bad C.  Besides being unportable and leaking memory, it may
have lead to someone's backup directory getting deleted (?).

Tweaked some error recovery code to make it more like 0.8.0.

Improved the installation a bit.


New in v0.9.0 (2002/06/17)
--------------------------

Changed lots of the code to distribute as standard python package
instead of single script.  Installation procedure is also different.

Speed optimizations - average user might see speed increase of 2 or
more.


New in v0.8.0 (2002/06/14)
--------------------------

Added --null-separator argument so filenames can safely include
newlines in an include/exclude filelist.

Fixed bug that affected restoring from current mirror with the '-r
now' option.


New in v0.7.6 (2002/05/31)
--------------------------

Improved statistics support, and added --print-statistics and
--calculate-average switches.  See the directory_statistics and
session_statistics files in the rdiff-backup-data directory.

Major improvements to error correction and resuming.

Now signals SIGQUIT, SIGHUP, and SIGTERM are caught to exit more
gracefully.

Fixed crankyness when --exclude-filelist is the last exclude option
and it is given an empty file (thanks to Bryce C for report).


New in v0.7.5 (2002/05/21)
--------------------------

Fixed resuming bug.

After a bit of empirical testing, increased Globals.conn_bufsize and
enabled ssh compression by default (and also added
--ssh-no-compression option).  This should speed up the "typical"
remote session.

Fixed bug noticed by Dean Gaudet in processing of
--(include|exclude)-filelist[-stdin] options when source directory was
remote.

Fixed --include error reporting bug reported by Ben Edwards.

Small change so 'door' files and other unknown file types will be
ignored.  (Thanks for Steve Simitzis for sending in a patch for this.)

Fixed bug noticed by Dean Gaudet where, unless the
--change-source-perms option is specified, rdiff-backup wouldn't even
attempt to open files lacking ownership permissions.


New in v0.7.4 (2002/05/11)
--------------------------

Added new restore syntax and corresponding -r and --restore-as-of
options.  For instance, "rdiff-backup -r 1/3/2002 /backup/foo out"
will try to restore /backup/foo (a file on the mirror directory) to
out, as it was January 3rd, 2002.  See man page for more information.

directory_statistics.<time>.data files will now be created in the
directories underneath rdiff-backup-data/increments.  Just look at one
to see what's inside.

Added extra options --chars-to-quote, --quoting-char, and
--windows-mode, mostly to allow files whose names have colons (:) in
them to be backed up to windows machines.

Now the -l and --list-increments switches can list the increments
corresponding to any mirror file, not just the root directory.  Also
the option --parsable-output was added to control whether the
--list-increments output looks better for a human, or computer.

Improved remove-earlier-than handling so it should run approximately
as fast locally and remotely.

Probably fixed bug noticed by Erminio Baranzini which caused
rdiff-backup to try to preserve access times unnecessarily (the
default is not preserve access times).

Rewrote a few large chunks of code for clarity and simplicity.

Allow extended time strings for the --remove-older-than option.

Added RESTORING section to the manual page because there seemed to be
some general confusion about this.

hardlink_data, current_mirror, and a few other files now carry the
.data extension (instead of .snapshot), to make it clearer they are
not copies of source files.


New in v0.7.3 (2002/04/29)
--------------------------

Fixed broken remote operation in v0.7.2 by applying (a variant of)
Daniel Robbins' patch.  Also fixed associated bug in test set.

Fixed bug recognizing --[include|exclude]-filelist-stdin options, and
IndexError bug reading some filelists.

--force is no longer necessary if the target directory is empty.

--include/--exclude/etc now work for restoring as they do for backing up.

Raised verbosity level for traceback output - if long log error
messages are annoying you, set verbosity to 2.  Will come up with a
better logging system later.

May have fixed a problem encountered by Matthew Farrellee and Kevin
Spicer wherein the _session_info_list information was stored on the
wrong computer.  This could cause rdiff-backup to fail when running
after another backup that failed for a different reason.  May backport
this fix to 0.6.0 later.

May have fixed a problem also noticed by Matthew Farrellee which can
cause rdiff-backup to exit when a directory changes into a
non-directory file while rdiff-backup is processing the directory.
(May also apply to 0.6.0).

Fixed a bug noticed by Jamie Heilman where restoring could fail if a
recent rdiff-backup process which produced the backup set was aborted
while processing a new directory.  (May also apply to 0.6.0)


New in v0.7.2 (2002/04/11)
--------------------------

Added new selection options --exclude-filelist,
--exclude-filelist-stdin, --exclude-regexp, --include-filelist,
--include-filelist-stdin, --include-regexp.

*** WARNING *** the --include and --exclude options have changed.  The
new --include-regexp and --exclude-regexp are close to, but still
different from the old --include and --exclude options.  See the man
page for details.

Friendlier error reporting when remote connection doesn't start.


New in v0.7.1 (2002/03/25)
--------------------------

Now by default .snapshot and .diff increments are compressed with
python's internal gzip.  The new increments format is backwards
compatible, but only rdiff-backup >0.7.1 will be able to restore if
any gzipped increments are present.

Added --no-compression and --no-compression-regexp to control which
files are compressed.


New in v0.7.0 (2002/03/21)
--------------------------

Added hardlink support.  This is now the default, but can be turned
off with --no-hardlinks.

Clarified a bit of the manual.

May have fixed a bug with remote handling of device files.


New in v0.6.0 (2002/03/14)
--------------------------

Fixed some assorted manual "bugs".

Fixed endless loop bug in certain error recovery situation reported by
Nick Duffek, and slightly changed around some other error correction
code.

Switching to new version numbering system:  versions x.2n+1.x are
unstable, versions x.2n.x are supposed to be more stable.


New in v0.5.4 (2002/03/06)
--------------------------

Fixed bug present since 0.5.0 wherein rdiff-backup would make
snapshots instead of diffs when regular files change.

May have fixed race condition involving rdiff execution.


New in v0.5.3 (2002/03/03)
--------------------------

It turns out the previous version broke device handling.  Sorry about
that..


New in v0.5.2 (2002/03/02)
--------------------------

Fixed bugs which made rdiff-backup try to preserve mod times when it
wasn't necessary, and exit instead of warning when it wasn't being run
as root and found a file it didn't own.  (Reported by Alberto
Accomazzi.)

Added some more error checking; maybe this will fix a bug reported by
John Goerzen wherein rdiff-backup can crash if file is deleted while
rdiff-backup is processing it.

Changed locations of some of the temp files; filenames will be
determined by the tempfile module.


New in v0.5.1 (2002/02/22)
--------------------------

When establishing a connection, print a warning if the server version
is different from the client version.

When find rdiff error value 256, tell user that it is probably because
rdiff couldn't be found in the path.

Fixed a serious bug that can apparently cause a remote backups to fail
(reported by John Goerzen).

May have fixed a bug that causes recovery from certain errors to fail.


New in v0.5.0 (2002/02/17)
--------------------------

Now every so often (default is 20 seconds, the --checkpoint-interval
option controls it) rdiff-backup checkpoints by dumping its state to
temporary files in the rdiff-backup-data directory.  If rdiff-backup
is rerun with the same destination directory, it can either try to
resume the previous backup or at least clean things up so the archive
is consistent and accurate.

Added new options --resume, --no-resume, and --resume-interval, which
control when rdiff-backup tries to resume a previous failed backup.

Fixed a bug with the --exclude-device-files option which caused the
option to be ignored when the source directory was remote.

By default, if rdiff-backup encounters a certain kind of IOError
(currently types 26 and 5) while trying to access a file, it logs the
error, skips the file, and tries to continue.

If settings requiring an integer argument (like -v or
--checkpoint-interval) are given a bad (non-integer) argument, fail
with better explanation.

Fixed annoying logging bug.  Now no matter which computer a logging
message originates on, it should be routed to the process which is
writing to the logging file, and written correctly.  However, logging
messages about network traffic will not be routed, as this will
generate more traffic and lead to an infinite regress.

When calling rdiff, uses popen2.Popen3 and os.spawnvp instead of
os.popen and os.system.  This should make rdiff-backup more secure.
Thanks to Jamie Heilman for the suggestion.

Instead of calling the external shell command 'stat', rdiff-backup
uses os.lstat().st_rdev to determine a device file's major and minor
numbers.  The new method should be more portable.  Thanks to Jamie
Heilman for the suggestion.

All the file operations were examined and tweaked to try to
minimize/eliminate the chance of leaving the backup directory in an
inconsistent state.

Upon catchable kinds of errors, try to checkpoint before exiting so
later rdiff-backup processes have more information to work with.

At the suggestion of Jason Piterak, added a --windows-time-format
option so rdiff-backup will (perhaps) work under MS windows NT.


New in v0.4.4 (2002/01/09)
--------------------------

Applied Berkan Eskikaya's "xmas patch" (I was travelling and didn't
have a chance on Christmas).  He fixed important bugs in the
--terminal-verbosity and --remove-older-than options.

Added an --exclude-device-files option, which makes rdiff-backup skip
any device files in the same way it skips files selected with the
--exclude option.


New in v0.4.3 (2001/12/17)
--------------------------

Plugged another memory hole.  At first I thought it might have been
python's fault, but it was all me.  If rdiff-backup uses more than a
few megabytes of memory, tell me because it is probably another memory
hole..

rdiff-backup is now a bit more careful about deleting temporary files
it creates when it is done with them.

Changed the rpm spec a little.  The enclosed man page is gzipped and
the package file is GPG signed (it can be checked with, for example,
"rpm --checksig -v rdiff-backup-0.4.3-1.noarch.rpm").

rdiff-backup no longer checks the mtimes or atimes of device files.
Use of these times was inconsistent (sometimes writing to device files
updates their times, sometimes not) and leads to unnecessary backing
up of files.


New in v0.4.2 (2001/11/19)
--------------------------

Significant speed increases (maybe 20% for local sessions) when
dealing with directories that do not need to be updated much.

Fixed memory leak.  rdiff-backup should now run in almost constant
memory (about 6MB on my system).

Enabled buffering of object transfers, so remote sessions can be
50-100%+ faster.

rdiff-backup now thinks it is running as root if the destination
connection is root.  Thus rdiff-backup will preserve ownership even if
it is not running as root on the source end.

If you abort rdiff-backup or it fails for some reason, it is now more
robust about recovering the next time it is run (before it could fail
in ways which made subsequent sessions fail also).  However, it is
still not a good idea to abort, as individual files could be in the
process of being written and could get corrupted.

If rdiff-backup encounters an unreadable file (or, if
--change-source-perms is given, a file whose permissions it cannot
change), it will log a warning, ignore the file, and continue, instead
of exiting with an error.


New in v0.4.1 (2001/11/9)
-------------------------

Now either the source, or the target, or both can be remote.  To make
this less confusing, now rdiff-backup supports host::file notation.
So it is legal to run:

rdiff-backup bill@host1.net::source_file jones@host2.net::target

Also, the test suites have been improved and found a number of bugs
(which were then fixed).


New in v0.4.0 (2001/11/4)
-------------------------

Much of the rdiff-backup internals were rewritten.  The result should
be better performance when operating remotely over a pipe with
significant latency.  Also the code dealing with changing permissions
is much cleaner, and should generalize later to similar jobs (for
instance preserving atimes.)

Listing and deleting increments and restoring should work remotely
now.  In earlier versions a file or directory had to be restored
locally and then copied over to its final destination.

At the request of the FSF, a copy of the GPL has been included in the
packaged distributions.  It is in the file "COPYING".


New in v0.3.4 (2001/10/31)
--------------------------

A change in python from the 2.2a series to 2.2b series made remote
backup on version 0.3.3 stop work, a small change fixes it.  (Thanks
to Berkan Eskikaya for telling me about this.)

Listed some missing features/bugs on the manual page.


New in v0.3.3 (2001/10/16)
--------------------------

Changed quoting system yet again after learning that the old system
was not very portable between shells (thanks Hans
<hguevremont@eternitee.com>)


New in v0.3.2 (2001/10/9)
-------------------------

Added --list-increments and --remove-older-than commands.
--list-increments will just tell you what increments you have and
their dates.  This isn't anything you couldn't get from "ls", but it
may be formatted more nicely.  The --remove-older-than command is used
to delete older increments that you don't want, or don't have space
for.

Also, on some systems ssh was adding a spurious "Broken pipe" message,
even though everything went fine.  Maybe this version will prevent
this confusing message.


New in v0.3.1 (2001/9/11)
-------------------------

Fix for stupid bug - when running remotely as users with different
uids, rdiff-backup now doesn't check the uid/gid.  Before it kept
thinking that the files needed to be updated because they didn't have
the right ownership.  This shouldn't have resulted in any data loss -
just some unnecessary .rdiff files.  (Thanks to Michael Friedlander
for finding this.)

Added check to make sure that rdiff exits successfully.


New in v0.3.0 (2001/9/9 - Billennium edition)
---------------------------------------------

rdiff-backup has been almost completely rewritten for v0.3.0, as it
was for v0.1.0.  The main problem with versions 0.2.x was that the
networking code was added to the not-remote-capable v0.1, and the
result was unwieldy and prone to bugs when operating over a pipe.

There are some new features:

- Hopefully very few bugs, at least in basic file handling.
  rdiff-backup has an extensive testing suite now, so it should be
  much more reliable.

- Complete support for reading and writing from and to files and
  directories that lack permissions, by temporarily changing them, and
  then changing them back later.  (See for instance the
  --change-source-perms switch.)  As I found out there is a lot to
  this, so much that I'm not sure in retrospect I should have
  bothered. :-)

- New more standard format for increment files.  See
  https://www.w3.org/TR/NOTE-datetime for the time standard.  The old
  format, besides being less standard, didn't take timezones into
  account.

- In the initial mirroring, rdiff-backup only copies the files that it
  needs to, so it is much quicker when you almost have an initial
  mirror already.  You can even the --mirror-only switch and make
  rdiff-backup into a slow version of rsync.

- Terminal and file verbosity levels can be selected separately.  So
  if you like a lot in your backup.log/restore.log but not much on
  your terminal, or vice-versa, you can set them at different numbers.

- New --test-server option so if something goes wrong you can see if
  it is because the server on the other side isn't being initialized
  properly.

- New --no-rdiff-copy option, which disables using rdiff to move files
  across a connection (it will still be used to make increment files
  however).  If the bottleneck is not bandwidth but local disks/CPUs,
  this options should speed things up.

There are, however, a few negatives:

- rdiff-backup now requires Python version 2.2 or later.  Sorry for
  the inconvenience but I use the new features a lot.

- It may be slightly slower overall than versions 0.2.x - the remote
  code is cleaner, but probably has higher overhead.  At least on my
  computer, rdiff-backup is still quicker than rsync for local
  mirroring of large files, but for remote mirroring, rsync will
  usually be much quicker, because it uses a fairly low-overhead
  pipelining protocol.

- Any old increments are incompatible because they use a different
  date/time standard.  If this is a big deal, try mailing me.  A
  converter shouldn't be very difficult to write, but I didn't want to
  take the time unless someone really wanted it.


New in v0.2.8 (2001/9/4)
-------------------------

Fixed two stupid bugs that would cause rdiff-backup to exit with an
exception.  (I can't believe they were in there.)


New in v0.2.7 (2001/8/29)
-------------------------

Added new long options --backup-mode and --verbosity which are
equivalent to -b and -v.

rdiff-backup should be a little more resistant to the filesystem it is
backup up changing underneath it (although it is not setup to handle
this in general).  Thanks Alberto Accomazzi
<aaccomazzi@cfa.harvard.edu> for these suggestions.


New in v0.2.6 (2001/8/27)
-------------------------

Fixed bug where, for non-root users, rdiff-backup could, in the
process of mirroring an unwritable directory, make the copy
unwriteable and then fail.  Now rdiff-backup goes through and makes
what it needs to be readable and writeable, and then changes things
back at the end.  (Another one found by Jeb Campbell!)


New in v0.2.5 (2001/8/26)
-------------------------

Added better error reporting when server throws an exception.

Fixed bug so that backed-up setuid files will also be setuid.

Now rdiff-backup thinks it's running as root only if both client and
server are running as root (Thanks to Jeb Campbell for finding these
previous two bugs).

Fixed miscellaneous Path bug that could occur in remote operation.


New in v0.2.4 (2001/8/25)
-------------------------

Added more logging options that may help other track down a mysterious
bug.


New in v0.2.3 (2001/8/24)
-------------------------

Fixed typing bug that caused an Assertion Error in remote operation,
thanks again to Jeb Campbell for finding it.


New in v0.2.2 (2001/8/24)
-------------------------

Fixed bug in remote creation of special files and symlinks (thanks to
Jeb Campbell <jebc@c4solutions.net> for finding it).

Fixed another error report.


New in v0.2.1 (2001/8/7)
------------------------

Now if rdiff-backup isn't running as root, it doesn't try to change
file ownership.

Fixed an error report.

Stopped flushing an open pipe to fix a race condition on IRIX.


New in v0.2 (2001/8/3)
----------------------

rdiff-backup can now operate in a bandwidth efficient manner (a la
rsync) using a pipe setup with, for instance, ssh.

I was too hasty with the last bug fix and didn't deal with all
filenames properly.  Maybe this one will work.


New in v0.1.1 (2001/8/2)
-------------------------

Bug fix:  Filenames that may contain spaces, backslashes, and other
special characters are quoted now and should be handled correctly.


New in v0.1 (2001/7/15)
----------------------

Large portion (majority?) of rdiff-backup was rewritten for v0.1.  New
version highlights:

 -  No new features!
 -  No speed improvements!  It may even be slower...
 -  No bug fixes!  (ok maybe a few)

However, the new version is much cleaner and better documented.  This
version should have fewer bugs, and it should be easier to fix any
future bugs.

