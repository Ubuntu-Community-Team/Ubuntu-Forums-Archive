---
title: "Dvdwizard"
date: 2009-06-22
forum: Multimedia Software
---

### Post by chmacka on 2009-06-22
How do I start DVDWIZARD?

I found the link  [here]("http://ubuntuforums.org/showthread.php?t=652843") and downloaded this deb: [http://dvdwizard.wershofen.net/index.php?option=com_frontpage&Itemid=1](http://dvdwizard.wershofen.net/index.php?option=com_frontpage&Itemid=1)

I installed it but I can't find it under Applications menu. When I run dvdwizard from the terminal I get this:

```
Usage:    dvdwizard [options] mpeg-file(s)
    dvdwizard -h|--help
    dvdwizard -v|--version

miscellaneous options:
----------------------
-h  | --help           print this lot out
-v  | --version        print version and exit

general processing:
-------------------
-C  | --config-file    filename of dvdwizard-configuration file
            [~/.dvdwizard/dvdwizard.conf]
-o  | --output        Path where the final DVD will be stored 
            [$BASEDIR/dvd]
-x  | --xml        Print dvdauthor XML-specs into this file
            [$BASEDIR/dvdwizard.xml]
-l  | --logfile        Write Log-Messages to this file 
            [$BASEDIR/dvdwizard.log]
-y  | --yes        Allow all target directories to be overwritten
--restart        Do not start from beginning but from step x
            x may be dvdcpics, mk_vmgm, mk_vtsm, author
--xmlonly        Do not author final DVD, only create menus and xml
            and remove temp. DVD structure.
--xmlkeep        Like --xmlonly, but keep temp. DVD structure

Note: $BASEDIR defaults to the current directory if not stated otherwise in the config file (either default ~/.dvdwizard/dvdwizard.conf or specified with the -C option)

DVD-specific options:
---------------------
-T  | --vmgm <string>    Titlestring for the whole DVD
            if not specified, no title will be printed on the 
            main menu
-N  | --tvnorm        TV-Norm to use <PAL|NTSC> [PAL]
-V  | --tvsize        Visible Area on TV-Screen <XxY> [635x535]
-WS                 Widescreen-Option (nopanscan or noletterbox) 
            for whole DVD may be overwritten by -ws for a 
            specific titleset
-P  | --palette      Name of palette File, needed i. E. for subpictures
-A  | --Audio        language for audiotracks. <lang1,lang2,...,langn> 
            [de,en]; languages are applied to audiotracks in 
            order they appear in the mpeg stream.
            applies to all titlesets on the DVD, may be 
            overwritten by -a for a specific titleset
-M  | --menu        Language to use in menu items [en]
            Textelements are defined in config file
-I  | --intro        MPEG-File to be played when inserting the DVD in 
            the player
-L  | --loop        Playback mode of the DVD. Possible values:
             0 - return to vmgm menu after each title
            -1 - display vmgm menu before the first and after 
                 the last title
            -2 - display vmgm menu only before first title and 
                 loop through all titles afterwards
            >0 - suppress vmgm menu and loop all titles 
                 endlessly, starting from specified title
-MS | --vmgmsound    Soundfile to be used as background sound for all 
            menus (may be overwritten for specific titlesets
            with -ms|--vtsmsound). If empty, a silent audio
            track will be produced.
            Can be any format, ffmpeg recognizes and will be
            converted to ac3, if neccessary.

Title-specific options:
-----------------------
-t  | --vts        Create a new titleset on the DVD with the subsequent
            options and mpeg-files.
            -t must be followed by a filename or a string or the
            word "auto"; "auto" determines title-string from 
            filename of first mpeg-file, if -t is followed by an
            existing filename, that file is considered to be the
            first mpeg in this titleset, else the string is used
            as movie title for this titleset
-c  | --chapters    Chapter-Specification <0|file|timecodes|interval> 
            [300]; 0 means no chaptering except for different 
            mpeg-files
-b  | --vtsmbg        Background-Picture for all menus concerning this 
            titleset
-ws                 Widescreen-Option (nopanscan or noletterbox) for 
            this titleset
-a  | --audio        see -A, but only applies to this titleset
-s  | --subpic       pass subpicture information to dvdauthor.
                    This is a string like "en" for english, "de" for 
                    German etc.
                    More Languages by Comma Separation, i.e. "-s de,en".
                    Each language may be followed by an optional "+hi" 
                    to indicate a subpicture track for hearing impaired,
                    i.e. "-s de,de+hi"
-i  | --info <file>      points to a text file containing description and the
            like for the movie            
-ms | --vtsmsound    see -MS, but only applies to this titleset

Note: Every new "-t" creates a new titleset on the DVD. Subsequent options -c, -b and -a and mpeg-file(s) apply only to that titleset. To create a DVD with 2 titlesets, use for example:
    dvdwizard -t auto -c 30 title1.mpg -t auto -b bckgrnd.ppm title2.mpg

```
How do I use it? Does it have GUI? According to this, it should have:

[I]Tutorial 

Insert what your movie in the list, you can put what you want mov avi wmv etc... , if you like you can create a video from your picture.., choose your music for Main menu, choose Titile, and Temp folder (/tmp), the output folder 
then click on the Dvd picture.
it will start to encode, build the menu and then it starts k3b [/I]

---

