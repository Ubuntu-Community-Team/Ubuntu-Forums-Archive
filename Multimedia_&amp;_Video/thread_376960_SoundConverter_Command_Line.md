---
title: "SoundConverter Command Line"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by StewD on 2007-03-05
Hi,

I am trying to write a shell script to automatically copy mp2 files, that have been recorded onto a memory card, into a single directory on my Ubuntu machine. The script should then use the SoundConverter application to convert all the mp2 files into mp3 files.

The copying of the files works well, however, my ability to manipulate the command line for SoundConverter is somewhat lacking.

I have tried the following (and a whole load of variations!!)

```
 soundconverter -b -m audio/mp3 -s .mp3 /home/SimsFiles/Radio/FromBug/02261359.mp2
```

but receive the following
```
SoundConverter 0.9.4
  using Gstreamer version: 0.10.10, Python binding version: 0.10.5
  using gnomevfssrc
Traceback (most recent call last):
  File "/usr/local/bin/soundconverter", line 2429, in ?
    main()
  File "/usr/local/bin/soundconverter", line 2425, in main
    cli_convert_main(args)
  File "/usr/local/bin/soundconverter", line 2315, in cli_convert_main
    c.init()
  File "/usr/local/bin/soundconverter", line 996, in init
    encoder = self.encoders[self.output_type]()
KeyError: 'audio/mp3'

```

How can I find out the relevant argument to replace "audio/mp3"? I've tried without the -m switch, but just get a different error:

```
SoundConverter 0.9.4
  using Gstreamer version: 0.10.10, Python binding version: 0.10.5
  using gnomevfssrc
overwriting 'file:///home/SimsFiles/Radio/FromBug/02261359.mp3'
02261359.mp2: /error: Could not determine type of stream. (02261359.mp2)
```

Can anyone advise on a command to convert a directory of mp2's to mp3's? Or point me to more documentation on the SoundConverter program's command line - ideally with some examples!!

I've also include the man page below in case it helps anyone decode my poor attempts at this.

Thanks in advance.

Stew


```

Usage: /usr/local/bin/soundconverter [options] [soundfile ...]

         -h, --help
           Print out a usage summary.

         -b, --batch
           Convert in batch mode, from command line, without a graphical user
           interface. You can use this from, say, shell scripts.

         -m arg, --mime-type=arg
           Set the output MIME type for batch mode. The default is
           audio/x-vorbis . Note that you probably want to set  the output suffix
           as well.

         -q, --quiet
           Be quiet. Don't write normal output, only errors.

         -d, --debug
           Print additionnal debug information

         -s arg, --suffix=arg
           Set the output filename suffix for batch mode. The default is   .ogg .
           Note that the suffix does not affect  the output MIME type.

         -t, --tags
           Show tags for input files instead of converting them. This indicates
           command line batch mode and disables the graphical user interface

```

---

### Post by mdjohnson on 2007-03-15
Try audio/mpeg

I'm racking my brains here, I think that worked for me in the past.

---

