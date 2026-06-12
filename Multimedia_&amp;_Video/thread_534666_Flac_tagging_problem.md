---
title: "Flac tagging problem"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by EGR on 2007-08-25
Hi everyone,

I'm currently in the process of ripping my CD collection to flac, using
abcde. The ripping itself is going well, and I'm pleased with the
results. Tagging, however, doesn't seem to work as it should: files get
ripped to the main music folder I specify, but only appear as
`track**.flac'. The CDDB file seems in order (I'm even prompted to
manually edit it when the script launches), so the problem doesn't seem
to be there. When it finishes running I get the following error-messages:
```

/home/eg/music/abcde.7510dd08/track08.flac: ERROR: memory allocation failure
[ERROR] abcde: The following commands failed to run:
tagtrack-flac-01: returned code 1: metaflac --no-utf8-convert --import-tags-from=- /home/eg/music/abcde.7510dd08/track01.flac
tagtrack-flac-02: returned code 1: metaflac --no-utf8-convert --import-tags-from=- /home/eg/music/abcde.7510dd08/track02.flac
tagtrack-flac-03: returned code 1: metaflac --no-utf8-convert --import-tags-from=- /home/eg/music/abcde.7510dd08/track03.flac
tagtrack-flac-04: returned code 1: metaflac --no-utf8-convert --import-tags-from=- /home/eg/music/abcde.7510dd08/track04.flac
tagtrack-flac-05: returned code 1: metaflac --no-utf8-convert --import-tags-from=- /home/eg/music/abcde.7510dd08/track05.flac
tagtrack-flac-06: returned code 1: metaflac --no-utf8-convert --import-tags-from=- /home/eg/music/abcde.7510dd08/track06.flac
tagtrack-flac-07: returned code 1: metaflac --no-utf8-convert --import-tags-from=- /home/eg/music/abcde.7510dd08/track07.flac
tagtrack-flac-08: returned code 1: metaflac --no-utf8-convert --import-tags-from=- /home/eg/music/abcde.7510dd08/track08.flac

```

Here's what my .abcde.conf file looks like:
```

##Rip to flac
OUTPUTTYPE=flac
INTERACTIVE=y
FLACOPTS='-8 -T'  
PADTRACKS=y
OUTPUTDIR="$HOME/music/"
ID3=/usr/bin/id3    
ID3V2=/usr/bin/id3v2 
CDPARANOIA=/usr/bin/cdparanoia     
CDDISCID=/usr/bin/cd-discid        
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
  }
  EXTRAVERBOSE=y           
  EJECTCD=y                          

```


Someone knows what I'm doing wrong?
Thanks!!

EDIT:
Ok, I've diagnosed the problem: for some reason, it's
characters like umlauts that are causing trouble. If I edit the file
names and replace instances of, say, `ü' with `ue' everything gets
tagged perfectly. I suppose there is some way of getting the tags
right automatically. Reading the error message it looks like it's
trying to tag with the `no-utf8' option enabled. I haven't set that
option anywhere. Is it some kind of default? If so, where do I turn it
off?

---

### Post by Klark Kockworth on 2007-08-26
Your tagging problem sounds similar to mine. I'm also ripping my albums with abcde and have trouble with umlauts. See [_my thread_]("http://ubuntuforums.org/showthread.php?t=534603") for details.

If you find a solution, let me know.

---

