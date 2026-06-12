---
title: "Mythrename problem"
date: 2009-02-07
forum: Mythbuntu
---

### Post by toddk111 on 2009-02-07
I'm using mythrename as follows:

mythrename.pl --verbose --format "%Y%-%m%-%d%-%H%i%-%T"

Here is an example of the renamed file:

2009-02-05-1955- Smallville- Supernatural (Manual Record).mpg

I don't want and didn't have any spaces in my title and I don't want (Manual Record) in my title.  How do I fix this?
Thanks!

---

### Post by Ryan5.5.5 on 2009-02-22
> **toddk111 said:**
> I'm using mythrename as follows:

mythrename.pl --verbose --format "%Y%-%m%-%d%-%H%i%-%T"

Here is an example of the renamed file:

2009-02-05-1955- Smallville- Supernatural (Manual Record).mpg

I don't want and didn't have any spaces in my title and I don't want (Manual Record) in my title.  How do I fix this?
Thanks!

I think if you remove the - from the format it should get rid of the spaces?  Below are the options.
As for the manual record I think this is set from MythTV if you do a manual record of a show, maybe try editing the title in MythTV when you record the show.


All options:
 options:
--link [destination directory]
   If you would like mythrename.pl to work like the old mythlink.pl, specify
   --link and an optional pathname. If no pathname is given, links will be
   created in the show_names directory inside of the current mythtv data
   directory on this machine.  eg:
   /var/video/show_names/
   WARNING: ALL symlinks within the destination directory and its
   subdirectories (recursive) will be removed when using the --link option.
--live
   Include live tv recordings, affects both linking and renaming.
   default: do not link/rename live tv recordings
--format
   default:  %T %- %Y-%m-%d, %g-%i %A %- %S
   %T = title    (aka show name)
   %S = subtitle (aka episode name)
   %R = description
   %C = category (as reported by grabber)
   %c = chanid
   %U = recording group
   %y = year, 2 digits
   %Y = year, 4 digits
   %n = month
   %m = month, leading zero
   %j = day of month
   %d = day of month, leading zero
   %g = 12-hour hour
   %G = 24-hour hour
   %h = 12-hour hour, with leading zero
   %H = 24-hour hour, with leading zero
   %i = minutes
   %s = seconds
   %a = am/pm
   %A = AM/PM
   %- = separator character
   /   = directory/folder (path separator)
   * For end time, prepend an "e" to the appropriate time/date format code
     above; i.e. "%eG" gives the 24-hour hour for the end time.
    * For original airdate, prepend an "o" to the year, month, or day format
     codes above; i.e. "%oY" gives the year in which the episode was first
     aired.
    * A suffix of .mpg or .nuv will be added where appropriate.
    * To separate links into subdirectories, include the / format specifier
     between the appropriate fields.  For example, "%T/%S" would create
     a directory for each title containing links for each recording named
     by subtitle.  You may use any number of subdirectories in your format
     specifier.  If used without the --link option, "/" will be replaced
     with the "%-" separator character.
 --separator
    The string used to separate sections of the link name.  Specifying the
   separator allows trailing separators to be removed from the link name and
   multiple separators caused by missing data to be consolidated. Indicate the
   separator character in the format string using either a literal character
   or the %- specifier.
    default:  '-'
 --replacement
    Characters in the link name which are not legal on some filesystems will
   be replaced with the given character
    illegal characters:  \ : * ? < > | "
    default:  '-'
 --underscores
    Replace whitespace in filenames with underscore characters.
    default:  No underscores
 --verbose
    Print debug info.
    default:  No info printed to console
 --help
   Show this help text.

---

