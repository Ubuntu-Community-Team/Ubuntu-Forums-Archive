---
title: "Metaflac"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by mytwobears on 2008-03-30
Hi,

I have a cd.cue file and a cd.flac file, I used cuetools and shntools to split the flac file into individual tracks.  I would like to use metaflac to tag the track names with the corresponding names in the cd.cue file.  What is the appropriate command for this?  I have tried using the following:

cuetag cd.cue split-track*.flac


Which gives me this output:


metaflac: unrecognized option `--remove-vc-all'
metaflac: unrecognized option `--import-vc-from=-'
==============================================================================
metaflac - Command-line FLAC metadata editor version 1.1.4
Copyright (C) 2001,2002,2003,2004,2005,2006,2007  Josh Coalson

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
==============================================================================

This is the short help; for full help use 'metaflac --help'

Usage:
  metaflac [options] [operations] FLACfile [FLACfile ...]

Use metaflac to list, add, remove, or edit metadata in one or more FLAC files.
You may perform one major operation, or many shorthand operations at a time.

Options:
--preserve-modtime    Preserve the original modification time in spite of edits
--with-filename       Prefix each output line with the FLAC file name
                      (the default if more than one FLAC file is specified)
--no-filename         Do not prefix each output line with the FLAC file name
                      (the default if only one FLAC file is specified)
--no-utf8-convert     Do not convert tags from UTF-8 to local charset,
                      or vice versa.  This is useful for scripts.
--dont-use-padding    By default metaflac tries to use padding where possible
                      to avoid rewriting the entire file if the metadata size
                      changes.  Use this option to tell metaflac to not take
                      advantage of padding this way.
metaflac: unrecognized option `--remove-vc-all'
metaflac: unrecognized option `--import-vc-from=-'

Does anyone know the correct parameters to use for this command to work?  Thanks for your help.

---

### Post by mytwobears on 2008-04-03
Someone help :confused:

---

### Post by DocForbin on 2008-04-03
I use shnsplit. 

shnsplit -o flac -f sample.cue -t “%n - %t” sample.flac

---

