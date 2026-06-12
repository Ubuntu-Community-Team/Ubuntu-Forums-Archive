---
title: "Amarok AAC support (or lack thereof), or suggestions for an all-in-one music manager"
date: 2017-01-05
forum: Multimedia Software
---

### Post by rdragonrydr on 2017-01-05
Hello!

I have tried Banshee, Rhythmbox, Clementine, and Amarok to rip, transcode, and sync my music. (I am using a fresh install of Ubuntu Unity desktop 16.04). I have had problems with all of these programs.

I need a program capable of ripping CDs and syncing music to several devices in two main formats. Specifically, I would like to rip CDs at about 192 kbps (fair quality, but also nice on disk space) and transcode to my DSi in m4a AAC format at 128kbps (so it needs bitrate settings when syncing, AAC support, and USB mass storage support.) I also have a Sansa clip jam that I would like to have 192 kbps mp3 on. It is also set to some sort of USB mass storage mode, I believe. The MTP mode did not work very well last time. Eurgh.

I'd prefer Banshee or Amarok, ideally, but I cannot solve some problems with them to use them.




Banshee: Hangs on media import unless I disable almost all extensions. I can't seem to find one particular one at fault. I am unsure of its long-term stability. Would otherwise be my preferred choice. It deletes songs that aren't in my local library from my device, but it lets me import first if I choose, so I can avoid the problem. Lets me choose transfer/transcode bitrate. CD ripping works fine, at least now. Very old and my not be supported for long?

Does not automatically recognize mp3 players attached to the computer unless I write an is_audio_player file or use Amarok to do so. Will not transcode to AAC format either.


Rhythmbox: Seems to work well, but I cannot set bitrate settings when syncing to a device. Perhaps this is in the is_audio_player file (all of my devices use SD cards or show up as USB mass storage. I have had problems with MTP in the past), but I can't find much of the syntax for it, at least that will work here. I would prefer 192 or 128 kbps VBR (I need both, depending on which device I want to use).

Deletes songs from the device that aren't in the local library. Does NOT have an import option.

Recently (on the new installation) CD ripping seems all wonky. If I set it to rip with VBR, I get a quality slider from 0 to 9.9. I am unable to tell what these are supposed to correspond to, and my Google search turned up blank. The 0 setting results in 192kbps audio (Mp3 is the codec I am using), and 9.9 gives me 7kbps audio. I cannot hear the difference between these, so I suspect that the audio is not really the bitrate it reports, and this seems really counter-intuitive. Furthermore, the runtime of the song is incorrect in the ripped version. It does not correspond to the reported one in the rip pane, and is actually not the length of the song -- I tested. If I try CBR, I get incorrect bitrate (It does not equal my setting, and isn't even close) and the song length is still wrong.

Does not automatically recognize mp3 players attached to the computer unless I write an is_audio_player file or use Amarok to do so. Will work with my DSi.


Amarok: It allows automatic creation of the is_audio_player file via activating a device. This seems to make it recognizable to the other two players. This is the only way to make it show up, short of trying to write it myself. It says AAC is non-free and is greyed out for me. I do not know what program might be missing. I need AAC for the DSi, so that doesn't work. CD ripping works fine, I guess. It has a very nice options set for this. It does not seem to pull in the dependencies for the transcoding of music. Either it works or it doesn't. It works here, except for AAC, but it does not work at all on my raspberry pi. I worry that it may suddenly stop transcoding for no apparent reason, as I do not know what items are responsible or whether or not they will stay on my computer (other software installations conflicting, distribution upgrades...). This one lets me add songs to my device without worrying about deleting others.


Clementine: I believe that its AAC format did not work with my DSi. I have not tried its CD ripping. Its device detection works regardless of the is_audio_player file, but will place all songs in the device's root dir, causing major problems. I forget if its transcoding offers bitrate settings.
I am not considering using this one, but I mention it to forestall its suggestion.


TL;DR: Rhythmbox does not give proper transcoding settings and won't rip CDs now.
Banshee is seemingly unstable and likes to hang. It also will not detect the SD card for my DSi at all. I cannot tell if it supports AAC or not.
Amarok will not transcode to AAC. Otherwise, it looks like my best choice.
Clementine is somewhat weird to use. It does not respect song location, dumping songs straight into the root directory of the MP3 player.


I would appreciate help with getting one of these to work, ideally Amarok, but Banshee or Rhythmbox may work too.

Do you know how to get AAC working in Amarok (and what is needed for transcoding options to appear) or how to do so for Banshee?

I would be also happy to get CDs working with Rhythmbox, but its lack of transcoding bitrate quality options for AAC is very problematic. I would prefer help with Amarok or Banshee.

---

### Post by SeijiSensei on 2017-01-05
If you're not uncomfortable with the command line, I would rip the CDs to .wav, then transcode to AAC using ffmpeg.  I recently used ffmpeg to add an audio track to a video file using an input file in Ogg Vorbis with AAC as the output.

In general I prefer FLAC for audio which most modern players now support.

---

### Post by Yellow Pasque on 2017-01-05
Do you have libavcodec-ffmpeg-extra56 package installed? Hopefully, that will let Amarok encode AAC.

---

### Post by Keith_Helms on 2017-01-06
Sounds like you have multiple use cases and one program may not do all of that stuff well.

I keep all my music in directory trees (musicformat->albums|collections|soundtracks|classical|comedy->disc-folder->songs).

I use abcde from the command line to rip the discs and then encode to both flac and mp3 at the same time.  It also can do other formats like aac and vorbis.  I use rsync to keep the directory trees in sync between multiple systems and a couple of sd cards and usb drives.

At that point, I use whatever I want to play them.  A hardware usb player that uses an sd card and usually audacious on my ubuntu systems.

All it takes me to run abcde and encode to 2 formats is a tiny script that invokes it and a config file.
```
#!/bin/sh

abcde -c ~/bin/mp3_scripts/abcde.albums.conf -p -o mp3,flac
```

```
LAMEOPTS='-V0'

ID3TAGV=id3v2.3

FLACOPTS='-f --best'

OUTPUTDIR=/data

OUTPUTFORMAT='/music_${OUTPUT}/Albums/${ARTISTFILE}/${YEAR}-${ALBUMFILE}/${TRACKNUM}-${TRACKFILE}'

mungefilename ()
{
    # echo "$@" | sed s,:,\ -,g | tr \ / __ | tr -d \'\"\?\[:cntrl:\]
    echo "$@" | tr "/\"*{}[]:" ";' ()()-" | tr -d "\?" 
}
```

---

### Post by Yellow Pasque on 2017-01-06
So I fired up my 16.04 VM and tried to get amarok to enable AAC encoding.
I installed libavcodec-ffmpeg-extra56 and this enable new encoders in ffmpeg (aac libvo_aacenc), as expected. Amarok still would not allow trancoding to AAC. 

Next, I installed mp4v2-utils, faac and fdkaac in case Amarok was looking for one of those. No dice..
So I'll admit I'm stumped at the moment and I really have no idea what amarok is looking for to enable AAC encoding.

---

### Post by Yellow Pasque on 2017-01-06
[https://cgit.kde.org/amarok.git/tree/src/core/transcoding/formats/TranscodingAacFormat.cpp](https://cgit.kde.org/amarok.git/tree/src/core/transcoding/formats/TranscodingAacFormat.cpp)

Okay, so Amarok is looking for ffmpeg to report that it has libfaac encoder available.
ffmpeg has deprecated libfaac: [https://trac.ffmpeg.org/wiki/Encode/AAC](https://trac.ffmpeg.org/wiki/Encode/AAC)

Sigh...

---

### Post by rdragonrydr on 2017-01-06
That is frustrating! Should I file a bug report?

Yes, I did have [COLOR=#000000]libavcodec-ffmpeg-extra56 installed, but I guess it won't help if that's the case.

What nice standalone CD rippers are out there?[/COLOR]

---

### Post by Keith_Helms on 2017-01-06
> **rdragonrydr said:**
> That is frustrating! Should I file a bug report?

Yes, I did have [COLOR=#000000]libavcodec-ffmpeg-extra56 installed, but I guess it won't help if that's the case.

What nice standalone CD rippers are out there?[/COLOR]

[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

An excerpt from that page:

> **ABCDE**

 Those who want a no-nosense, fast, customizable ripping solution should try [ABCDE]("http://abcde.einval.com/wiki/"). 
And example conversion from CD to AAC/MP4: 
```
abcde -a cddb,read,encode,tag,move,playlist,clean -d /dev/cdrom -o m4a -V -x
```

---

### Post by Yellow Pasque on 2017-01-06
> That is frustrating! Should I file a bug report?

If you want. Have at it: [https://bugs.kde.org/enter_bug.cgi](https://bugs.kde.org/enter_bug.cgi)

> What nice standalone CD rippers are out there?
abcde is awesome, but I understand it's not for everyone.
For a good GUI ripper, I prefer Audex. I wouldn't want to rip to AAC using Audex because it also uses the old faac encoder. However, it seems like you're interested in ripping CD's to mp3, so Audex will let you do that with minimum fuss (assuming you have lame package installed).

> [https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

Wow, is that page outdated. It still shows sound juicer with bitrate options. LOL

---

### Post by andrew.46 on 2017-01-06
> **Keith_Helms said:**
> [https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

The only trouble with the command line syntax given on that page for AAC/m4a encoding is that it will use faac which has 2 issues:

[LIST=1]
[*]Under Debian/Ubuntu faac has had the ability to output to m4a removed
[*]faac is very, very low on the totem pole of sound quality with AAC encoding
[*]
[/LIST]

This has been corrected in abcde development where [fdkaac is the new default]("https://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=commit;h=50d328b2020be799fdad97aec424c8b049db22ef") but for the moment a suitable ~/.abcde.conf file will use fdkaac for AAC encoding and certainly as the OP has requested abcde can run both mp3 and AAC encoding at the same time...

---

### Post by Keith_Helms on 2017-01-06
What?  You mean there are instructions on the internet that are out of date???  ;)

Well, if the OP expresses interest in giving it a try, I assume you can point him to where he needs to download the development version of abcde.  I imagine it's somewhere in the 50-mile long endless thread:
[https://ubuntuforums.org/showthread.php?t=2257705](https://ubuntuforums.org/showthread.php?t=2257705)

---

### Post by andrew.46 on 2017-01-06
> **Keith_Helms said:**
> Well, if the OP expresses interest in giving it a try, I assume you can point him to where he needs to download the development version of abcde.

No need for the development version if a suitable ~/.abcde.conf file is used. The following will use fdkaac and lame to generate AAC and mp3 outputs as long as abcde 2.7 and greater is used:

```

# -----------------$HOME/.abcde.conf----------------- #
# 
#  A sample configuration file to convert music cds to 
#  MP3 and AAC at the same time. Requires lame, eyeD3,
#  fdkaac and abcde version 2.7 and greater...
# 
#      http://andrews-corner.org/linux/abcde.html
# -------------------------------------------------- #

# Encode tracks immediately after reading. Saves disk space, gives
# better reading of 'scratchy' disks and better troubleshooting of
# encoding process but slows the operation of abcde quite a bit:
LOWDISK=y

# Specify the method to use to retrieve the track information,
# the alternative is to specify 'musicbrainz':
CDDBMETHOD=cddb

# Make a local cache of cddb entries and then volunteer to use 
# these entries when and if they match the cd:
CDDBCOPYLOCAL="y"
CDDBLOCALDIR="$HOME/.cddb"
CDDBLOCALRECURSIVE="y"
CDDBUSELOCAL="y"

MP3ENCODERSYNTAX=lame                   # Specify encoder for MP3
AACENCODERSYNTAX=fdkaac                 # Specify encoder for AAC

LAME=lame                               # Path to MP3 encoder
FDKAAC=fdkaac                           # Path to the AAC encoder

LAMEOPTS='-V 2'                         # Options for MP3 
FDKAACENCOPTS='-p 2 -m 5 -a 1'          # Options for fdkaac

OUTPUTTYPE="mp3,m4a"                    # Encode to both formats!

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac. New to abcde 2.7 is 'libcdio'.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options,
# if using libcdio set 'CD_PARANOIA=cd-paranoia'.
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid           
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/Music"               

# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,encode,tag,move,clean

# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

# This function takes out dots preceding the album name, and removes a grab
# bag of illegal characters. It allows spaces, if you do not wish spaces add
# in -e 's/ /_/g' after the first sed command.
mungefilename ()
{
  echo "$@" | sed -e 's/^\.*//' | tr -d ":><|*/\"'?[:cntrl:]"
}

MAXPROCS=2                                # Run a few encoders simultaneously
PADTRACKS=y                               # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=2                            # Useful for debugging
COMMENT='Processed with abcde'            # Place a comment...
EJECTCD=y                                 # Please eject cd when finished :-)

```

The encoding options (and everything else) can be altered to please....

Mind you this is a long way from a music manager as the OP has requested.

---

### Post by Yellow Pasque on 2017-01-07
Personally, I don't use AAC for music, but I was able to whip up a very rough patch that allows Amarok to transcode to AAC if ffmpeg reports its 'aac' encoder available. The patch definitely needs fine tuning, especially in regards to controlling quality/bitrate (currently, it just spits out really high bitrate AAC-LC). It could also use a proper check of ffmpeg version and only use "-strict -2" parameters if ffmpeg version is < 3.0.
A more far-reaching goal may be to add an HE-AAC transocder if libfdk-aac if available

```
--- a/src/core/transcoding/formats/TranscodingAacFormat.cpp
+++ b/src/core/transcoding/formats/TranscodingAacFormat.cpp
@@ -89,12 +89,7 @@
 AacFormat::ffmpegParameters( const Configuration &configuration ) const
 {
     QStringList parameters;
-    parameters << "-acodec" << "libfaac"; /* libfaac seems to be the only decent AAC encoder
-                                             for GNU/Linux and it's a proprietary freeware
-                                             with LGPL portions. Hopefully in the future
-                                             FFmpeg's native aac implementation should get
-                                             better so libfaac won't be necessary any more.
-                                                            -- Teo 5/aug/2010 */
+    parameters << "-acodec" << "aac" << "-strict" << "-2";
     foreach( Property property, m_propertyList )
     {
         if( !configuration.property( property.name() ).isNull()
@@ -113,5 +108,5 @@
 bool
 AacFormat::verifyAvailability( const QString &ffmpegOutput ) const
 {
-    return ffmpegOutput.contains( QRegExp( "^ .EA....*libfaac" ) );
+    return ffmpegOutput.contains( QRegExp( "^ .EA....*aac" ) );
 }

```

EDIT: Thanks for reporting the bug: [https://bugs.kde.org/show_bug.cgi?id=374670](https://bugs.kde.org/show_bug.cgi?id=374670)
I'm hoping experienced KDE/Qt devs can resolve it a lot faster/better than I can.

---

### Post by Yellow Pasque on 2017-01-08
I made some progress.
```
--- a/src/core/transcoding/formats/TranscodingAacFormat.cpp
+++ b/src/core/transcoding/formats/TranscodingAacFormat.cpp
@@ -44,17 +44,17 @@
     QStringList valueLabels;
     QByteArray vbr = "VBR ~%1kb/s";
     valueLabels
-        << i18n( vbr, 25 )
-        << i18n( vbr, 50 )
-        << i18n( vbr, 70 )
-        << i18n( vbr, 90 )
-        << i18n( vbr, 120 )
-        << i18n( vbr, 150 )
-        << i18n( vbr, 170 )
-        << i18n( vbr, 180 )
-        << i18n( vbr, 190 )
-        << i18n( vbr, 200 )
-        << i18n( vbr, 210 );
+        << i18n( vbr, 8 )
+        << i18n( vbr, 32 )
+        << i18n( vbr, 64 )
+        << i18n( vbr, 96 )
+        << i18n( vbr, 128 )
+        << i18n( vbr, 160 )
+        << i18n( vbr, 192 )
+        << i18n( vbr, 224 )
+        << i18n( vbr, 256 )
+        << i18n( vbr, 288 )
+        << i18n( vbr, 320 );
     m_propertyList << Property::Tradeoff( "quality", i18n( "Expected average bitrate for variable bitrate encoding" ), description1,
                                           i18n( "Smaller file" ), i18n( "Better sound quality"),
                                           valueLabels, 6 );
@@ -89,12 +89,7 @@
 AacFormat::ffmpegParameters( const Configuration &configuration ) const
 {
     QStringList parameters;
-    parameters << "-acodec" << "libfaac"; /* libfaac seems to be the only decent AAC encoder
-                                             for GNU/Linux and it's a proprietary freeware
-                                             with LGPL portions. Hopefully in the future
-                                             FFmpeg's native aac implementation should get
-                                             better so libfaac won't be necessary any more.
-                                                            -- Teo 5/aug/2010 */
+    parameters << "-acodec" << "aac" << "-strict" << "-2";
     foreach( Property property, m_propertyList )
     {
         if( !configuration.property( property.name() ).isNull()
@@ -102,8 +97,8 @@
         {
             if( property.name() == "quality" )
             {
-                parameters << "-aq"
-                           << QString::number( configuration.property( "quality" ).toInt() * 25 + 5 );
+                parameters << "-b:a"
+                           << QString::number( configuration.property( "quality" ).toInt() * 32000);
             }
         }
     }
@@ -113,5 +108,5 @@
 bool
 AacFormat::verifyAvailability( const QString &ffmpegOutput ) const
 {
-    return ffmpegOutput.contains( QRegExp( "^ .EA....*libfaac" ) );
+    return ffmpegOutput.contains( QRegExp( "^ .EA....aac" ) );
 }

```

---

### Post by rdragonrydr on 2017-01-13
Hi again!

That looks quite nice. It does indeed look like a fix (to my limited knowledge of this, anyway), but I unfortunately don't know how to apply patches... Could you please let me know how to install that to to my copy of the source? (Sorry, I know I'm an idiot)

Also, could someone please confirm the bug over at the tracker? I just checked on it, and it is still unconfirmed, along with several others from years ago... I *really* don't want to be one of those people!

---

### Post by Yellow Pasque on 2017-01-14
I submitted the patch on your bug. I don't think I have permission to confirm it though.

As for testing it out, you copy/paste the text into a text file and apply it like so (assuming you called the file aacfix.patch):
```
cd amarok-2.8.0/
patch -p1 < aacfix.patch
```

I guess I could make a PPA or something, but it's been a long time since I've done that, or even had an active Launchpad account for that matter.

---

### Post by rdragonrydr on 2017-01-14
Thank you very much. I will go try that now! I don't think I need a PPA, but I do hope that the amarok devs add that in eventually.

---

### Post by rdragonrydr on 2017-01-15
FYI, Someone on the bug reporting site has asked that the patch be submitted to the review board and assigned to Amarok. I don't know if this is important.

---

### Post by Yellow Pasque on 2017-01-15
A rough attempt at HE-AAC. Unfortunately, I don't know enough about cmake to get it to all build properly and actually test it:
```
diff -rupN amarok/src/core/transcoding/formats/TranscodingHeaacFormat.cpp modified/src/core/transcoding/formats/TranscodingHeaacFormat.cpp
--- amarok/src/core/transcoding/formats/TranscodingHeaacFormat.cpp	1969-12-31 19:00:00.000000000 -0500
+++ modified/src/core/transcoding/formats/TranscodingHeaacFormat.cpp	2017-01-15 22:10:24.087360465 -0500
@@ -0,0 +1,112 @@
+/****************************************************************************************
+ * Copyright (c) 2010 Téo Mrnjavac <teo@kde.org>                                        *
+ *                                                                                      *
+ * This program is free software; you can redistribute it and/or modify it under        *
+ * the terms of the GNU General Public License as published by the Free Software        *
+ * Foundation; either version 2 of the License, or (at your option) any later           *
+ * version.                                                                             *
+ *                                                                                      *
+ * This program is distributed in the hope that it will be useful, but WITHOUT ANY      *
+ * WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A      *
+ * PARTICULAR PURPOSE. See the GNU General Public License for more details.             *
+ *                                                                                      *
+ * You should have received a copy of the GNU General Public License along with         *
+ * this program.  If not, see <http://www.gnu.org/licenses/>.                           *
+ ****************************************************************************************/
+
+#include "TranscodingHeaacFormat.h"
+
+#include <KLocale>
+
+#include <QVariant>
+
+using namespace Transcoding;
+
+HeaacFormat::HeaacFormat()
+{
+    m_encoder = HEAAC;
+    m_fileExtension = "m4a";
+    QString description1 =
+        i18n( "High Efficiency AAC is a special version of AAC that aims to provide reasonably "
+              "good audio quality at low bitrates. There are two versions of HE-AAC. Regular "
+              "HE-AAC, also known as HE-AACv1, is targeted at bitrates from about 64kb/s to 96kb/s. " 
+              "HE-AACv2 is targeted for bitrates below 64kb/s. Anything over 96kb/s is overkill, "
+              "and you should consider using AAC for maximum compatibility." );
+
+    QStringList valueLabels;
+    QByteArray vbr = "VBR ~%1kb/s";
+    valueLabels
+        << i18n( vbr, 16 )  //use HE-AACv2 for bitrates under 64kb/s
+        << i18n( vbr, 24 )
+        << i18n( vbr, 32 )
+        << i18n( vbr, 40 )
+        << i18n( vbr, 48 )
+        << i18n( vbr, 56 )
+        << i18n( vbr, 64 ) //use HE-AAC version1 for 64kb/s or greater
+        << i18n( vbr, 72 )
+        << i18n( vbr, 80 )
+        << i18n( vbr, 88 )
+        << i18n( vbr, 96 );
+
+    m_propertyList << Property::Tradeoff( "quality", i18n( "Target Bitrate" ), description1,
+                                          i18n( "Smaller file" ), i18n( "Better sound quality"),
+                                          valueLabels, 6 );
+}
+
+QString
+HeaacFormat::prettyName() const
+{
+    return i18n( "HE-AAC (Non-Free)" );
+}
+
+QString
+HeaacFormat::description() const
+{
+    return i18n( "High Efficiency AAC is a special version of AAC that aims to provide reasonably "
+              "good audio quality at low bitrates. There are two versions of HE-AAC. Regular "
+              "HE-AAC, also known as HE-AACv1, is targeted at bitrates from about 64kb/s to 96kb/s. " 
+              "HE-AACv2 is targeted for bitrates below 64kb/s. Anything over 96kb/s is overkill, "
+              "and you should consider using AAC for maximum compatibility." );
+
+}
+
+KIcon
+HeaacFormat::icon() const
+{
+    return KIcon( "audio-ac3" ); //TODO: get a *real* icon!
+}
+
+QStringList
+HeaacFormat::ffmpegParameters( const Configuration &configuration ) const
+{
+    QStringList parameters;
+    parameters << "-acodec" << "libfdk_aac";
+ 
+    foreach( const Property &property, m_propertyList )
+    {
+        if( !configuration.property( property.name() ).isNull()
+            && configuration.property( property.name() ).type() == property.variantType() )
+        {
+            if( property.name() == "quality" )
+            {
+                if( configuration.property( "quality" ).toInt() <= 5 )
+                {
+                    parameters << "-profile:a" << "aac_he_v2";
+                }
+                else
+                {
+                    parameters << "-profile:a" << "aac_he";
+                }
+                parameters << "b:a"
+                           << QString::number( (configuration.property( "quality" ).toInt() + 2) * 8000 );
+            }
+        }
+    }
+    return parameters;
+}
+
+bool
+HeaacFormat::verifyAvailability( const QString &ffmpegOutput ) const
+{
+    return ffmpegOutput.contains( QRegExp( "^ .EA....libfdk_aac" ) );
+}
diff -rupN amarok/src/core/transcoding/formats/TranscodingHeaacFormat.h modified/src/core/transcoding/formats/TranscodingHeaacFormat.h
--- amarok/src/core/transcoding/formats/TranscodingHeaacFormat.h	1969-12-31 19:00:00.000000000 -0500
+++ modified/src/core/transcoding/formats/TranscodingHeaacFormat.h	2017-01-15 21:06:18.636704565 -0500
@@ -0,0 +1,46 @@
+/****************************************************************************************
+ * Copyright (c) 2010 Téo Mrnjavac <teo@kde.org>                                        *
+ *                                                                                      *
+ * This program is free software; you can redistribute it and/or modify it under        *
+ * the terms of the GNU General Public License as published by the Free Software        *
+ * Foundation; either version 2 of the License, or (at your option) any later           *
+ * version.                                                                             *
+ *                                                                                      *
+ * This program is distributed in the hope that it will be useful, but WITHOUT ANY      *
+ * WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A      *
+ * PARTICULAR PURPOSE. See the GNU General Public License for more details.             *
+ *                                                                                      *
+ * You should have received a copy of the GNU General Public License along with         *
+ * this program.  If not, see <http://www.gnu.org/licenses/>.                           *
+ ****************************************************************************************/
+
+#ifndef TRANSCODING_HEAACFORMAT_H
+#define TRANSCODING_HEAACFORMAT_H
+
+#include "core/transcoding/TranscodingFormat.h"
+
+namespace Transcoding
+{
+
+/**
+ * This class implements the interface for the libfdk_aac HE-AAC (v1 and v2) encoder 
+ * through FFmpeg, as long as FFmpeg is compiled with support for the proprietary 
+ * FDK-AAC library.
+ * If a distro chooses to package FFmpeg without libfdk_aac support, this codec won't
+ 
+*/
+
+class AMAROK_CORE_EXPORT HeaacFormat : public Format
+{
+public:
+    HeaacFormat();
+    QString prettyName() const;
+    QString description() const;
+    KIcon icon() const;
+    QStringList ffmpegParameters( const Configuration &configuration ) const;
+    bool verifyAvailability( const QString &ffmpegOutput ) const;
+};
+
+}
+
+#endif // TRANSCODING_HEAACFORMAT_H
\ No newline at end of file
diff -rupN amarok/src/core/transcoding/TranscodingConfiguration.cpp modified/src/core/transcoding/TranscodingConfiguration.cpp
--- amarok/src/core/transcoding/TranscodingConfiguration.cpp	2017-01-15 20:10:27.521646764 -0500
+++ modified/src/core/transcoding/TranscodingConfiguration.cpp	2017-01-15 20:52:59.361308208 -0500
@@ -152,6 +152,7 @@ Configuration::encoderNames()
     s_encoderNames.insert( INVALID, QLatin1String( "INVALID" ) );
     s_encoderNames.insert( JUST_COPY, QLatin1String( "JUST_COPY" ) );
     s_encoderNames.insert( AAC, QLatin1String( "AAC" ) );
+    s_encoderNames.insert( HEAAC, QLatin1String( "HEAAC" ) );
     s_encoderNames.insert( ALAC, QLatin1String( "ALAC" ) );
     s_encoderNames.insert( FLAC, QLatin1String( "FLAC" ) );
     s_encoderNames.insert( MP3, QLatin1String( "MP3" ) );
diff -rupN amarok/src/core/transcoding/TranscodingController.cpp modified/src/core/transcoding/TranscodingController.cpp
--- amarok/src/core/transcoding/TranscodingController.cpp	2017-01-15 20:10:27.521646764 -0500
+++ modified/src/core/transcoding/TranscodingController.cpp	2017-01-15 22:12:06.227579672 -0500
@@ -18,6 +18,7 @@
 
 #include "formats/TranscodingNullFormat.h"
 #include "formats/TranscodingAacFormat.h"
+#include "formats/TranscodingHeaacFormat.h"
 #include "formats/TranscodingAlacFormat.h"
 #include "formats/TranscodingFlacFormat.h"
 #include "formats/TranscodingMp3Format.h"
@@ -33,6 +34,7 @@ Controller::Controller( QObject *parent
     m_formats.insert( JUST_COPY, new NullFormat( JUST_COPY ) );
     m_formats.insert( INVALID, new NullFormat( INVALID ) );
     m_formats.insert( AAC, new AacFormat() );
+    m_formats.insert( HEAAC, new HeaacFormat() );
     m_formats.insert( ALAC, new AlacFormat() );
     m_formats.insert( FLAC, new FlacFormat() );
     m_formats.insert( MP3, new Mp3Format() );
diff -rupN amarok/src/core/transcoding/TranscodingDefines.h modified/src/core/transcoding/TranscodingDefines.h
--- amarok/src/core/transcoding/TranscodingDefines.h	2017-01-15 20:10:27.521646764 -0500
+++ modified/src/core/transcoding/TranscodingDefines.h	2017-01-15 20:56:48.840073520 -0500
@@ -24,6 +24,7 @@ namespace Transcoding
         INVALID,   // denotes invalid transcoding configuration
         JUST_COPY, // just copy or move the tracks (no transcoding)
         AAC,       // Advanded Audio Coding
+        HEAAC,     // High Efficiency AAC
         ALAC,      // Apple Lossless Audio Codec
         FLAC,      // Free Lossless Audio Codec
         MP3,       // MPEG-1 or MPEG-2 Audio Layer III encoded using lame encoder
```

---

### Post by rdragonrydr on 2017-05-07
I just used the apt-get build-dep command, and disabled tests, since I did not have Google Mock installed. The compilation for He-AAC failed with an error on not finding Transcoding:HEAAC:HEAAC(), I believe. I can't figure out why, since all the code seems there and mirrors the one for regular AAC. I am testing the regular AAC fix now.

If you are still subscribed to this post, perhaps you can help me track down the error.

```
CMakeFiles/amarokcore.dir/transcoding/TranscodingController.cpp.o: In function `Transcoding::Controller::Controller(QObject*)':/home/rdragonrydr/heac/src/core/transcoding/TranscodingController.cpp:37: undefined reference to `Transcoding::HeaacFormat::HeaacFormat()'
collect2: error: ld returned 1 exit status
src/core/CMakeFiles/amarokcore.dir/build.make:1562: recipe for target 'lib/libamarokcore.so.1.0.0' failed
make[2]: *** [lib/libamarokcore.so.1.0.0] Error 1
CMakeFiles/Makefile2:1418: recipe for target 'src/core/CMakeFiles/amarokcore.dir/all' failed
make[1]: *** [src/core/CMakeFiles/amarokcore.dir/all] Error 2
Makefile:138: recipe for target 'all' failed
make: *** [all] Error 2



```

EDIT::


I also found that the AAC patch does not work. I posted some info about it on the bug report page too, but the gist is that the regex is searching for a specific list of supported formats (Audio and Encoder) but my installation also has decoder support. The regex can't seem to find it, as a result. At least, that's my guess, as I can't read regex. Can you help me fix this?

```
Codecs: D..... = Decoding supported
 .E.... = Encoding supported
 ..V... = Video codec
 ..A... = Audio codec
 ..S... = Subtitle codec
 ...I.. = Intra frame-only codec
 ....L. = Lossy compression
 .....S = Lossless compression
 -------
 D.VI.. 012v                 Uncompressed 4:2:2 10-bit
 D.V.L. 4xm                  4X Movie
 D.VI.S 8bps                 QuickTime 8BPS video
 .EVIL. a64_multi            Multicolor charset for Commodore 64 (encoders: a64multi )
 .EVIL. a64_multi5           Multicolor charset for Commodore 64, extended with 5th color (colram) (encoders: a64multi5 )
 D.V..S aasc                 Autodesk RLE
 D.VIL. aic                  Apple Intermediate Codec
 DEVI.S alias_pix            Alias/Wavefront PIX image
 DEVIL. amv                  AMV Video
 D.V.L. anm                  Deluxe Paint Animation
 D.V.L. ansi                 ASCII/ANSI art
 DEV..S apng                 APNG (Animated Portable Network Graphics) image
 DEVIL. asv1                 ASUS V1
 DEVIL. asv2                 ASUS V2
 D.VIL. aura                 Auravision AURA
 D.VIL. aura2                Auravision Aura 2
 D.V... avrn                 Avid AVI Codec
 DEVI.. avrp                 Avid 1:1 10-bit RGB Packer
 D.V.L. avs                  AVS (Audio Video Standard) video
 DEVI.. avui                 Avid Meridien Uncompressed
 DEVI.. ayuv                 Uncompressed packed MS 4:4:4:4
 D.V.L. bethsoftvid          Bethesda VID video
 D.V.L. bfi                  Brute Force & Ignorance
 D.V.L. binkvideo            Bink video
 D.VI.. bintext              Binary text
 DEVI.S bmp                  BMP (Windows and OS/2 bitmap)
 D.V..S bmv_video            Discworld II BMV video
 D.VI.S brender_pix          BRender PIX image
 D.V.L. c93                  Interplay C93
 D.V.L. cavs                 Chinese AVS (Audio Video Standard) (AVS1-P2, JiZhun profile)
 D.V.L. cdgraphics           CD Graphics video
 D.VIL. cdxl                 Commodore CDXL video
 DEV.L. cinepak              Cinepak
 DEVIL. cljr                 Cirrus Logic AccuPak
 D.VI.S cllc                 Canopus Lossless Codec
 D.V.L. cmv                  Electronic Arts CMV video (decoders: eacmv )
 D.V... cpia                 CPiA video format
 D.V..S cscd                 CamStudio (decoders: camstudio )
 D.VIL. cyuv                 Creative YUV (CYUV)
 D.VILS dds                  DirectDraw Surface image decoder
 D.V.L. dfa                  Chronomaster DFA
 DEV.LS dirac                Dirac (encoders: libschroedinger )
 DEVIL. dnxhd                VC3/DNxHD
 DEVI.S dpx                  DPX (Digital Picture Exchange) image
 D.V.L. dsicinvideo          Delphine Software International CIN video
 DEVIL. dvvideo              DV (Digital Video)
 D.V..S dxa                  Feeble Files/ScummVM DXA
 D.VI.S dxtory               Dxtory
 D.V.L. escape124            Escape 124
 D.V.L. escape130            Escape 130
 D.VILS exr                  OpenEXR image
 DEV..S ffv1                 FFmpeg video codec #1
 DEVI.S ffvhuff              Huffyuv FFmpeg variant
 D.V.L. fic                  Mirillis FIC
 DEV..S flashsv              Flash Screen Video v1
 DEV.L. flashsv2             Flash Screen Video v2
 D.V..S flic                 Autodesk Animator Flic video
 DEV.L. flv1                 FLV / Sorenson Spark / Sorenson H.263 (Flash Video) (decoders: flv ) (encoders: flv )
 D.V..S fraps                Fraps
 D.VI.S frwu                 Forward Uncompressed
 D.V.L. g2m                  Go2Meeting
 DEV..S gif                  GIF (Graphics Interchange Format)
 DEV.L. h261                 H.261
 DEV.L. h263                 H.263 / H.263-1996, H.263+ / H.263-1998 / H.263 version 2
 D.V.L. h263i                Intel H.263
 DEV.L. h263p                H.263+ / H.263-1998 / H.263 version 2
 DEV.LS h264                 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (decoders: h264 h264_crystalhd h264_vdpau ) (encoders: libx264 libx264rgb )
 DEVIL. hap                  Vidvox Hap decoder
 DEV.L. hevc                 H.265 / HEVC (High Efficiency Video Coding) (encoders: libx265 )
 D.V.L. hnm4video            HNM 4 video
 D.VIL. hq_hqa               Canopus HQ/HQA
 D.VIL. hqx                  Canopus HQX
 DEVI.S huffyuv              HuffYUV
 D.V.L. idcin                id Quake II CIN video (decoders: idcinvideo )
 D.VI.. idf                  iCEDraw text
 D.V.L. iff_byterun1         IFF ByteRun1 (decoders: iff )
 D.V.L. iff_ilbm             IFF ILBM (decoders: iff )
 D.V.L. indeo2               Intel Indeo 2
 D.V.L. indeo3               Intel Indeo 3
 D.V.L. indeo4               Intel Indeo Video Interactive 4
 D.V.L. indeo5               Intel Indeo Video Interactive 5
 D.V.L. interplayvideo       Interplay MVE video
 DEVILS jpeg2000             JPEG 2000 (encoders: jpeg2000 libopenjpeg )
 DEVILS jpegls               JPEG-LS
 D.VIL. jv                   Bitmap Brothers JV video
 D.V.L. kgv1                 Kega Game Video
 D.V.L. kmvc                 Karl Morton's video codec
 D.VI.S lagarith             Lagarith lossless
 .EVI.S ljpeg                Lossless JPEG
 D.VI.S loco                 LOCO
 D.V.L. mad                  Electronic Arts Madcow Video (decoders: eamad )
 D.VIL. mdec                 Sony PlayStation MDEC (Motion DECoder)
 D.V.L. mimic                Mimic
 DEVIL. mjpeg                Motion JPEG
 D.VIL. mjpegb               Apple MJPEG-B
 D.V.L. mmvideo              American Laser Games MM Video
 D.V.L. motionpixels         Motion Pixels video
 DEV.L. mpeg1video           MPEG-1 video (decoders: mpeg1video mpeg1video_vdpau )
 DEV.L. mpeg2video           MPEG-2 video (decoders: mpeg2video mpegvideo mpegvideo_vdpau mpeg2_crystalhd )
 DEV.L. mpeg4                MPEG-4 part 2 (decoders: mpeg4 mpeg4_crystalhd mpeg4_vdpau ) (encoders: mpeg4 libxvid )
 D.V.L. mpegvideo_xvmc       MPEG-1/2 video XvMC (X-Video Motion Compensation)
 D.V.L. msa1                 MS ATC Screen
 D.V.L. msmpeg4v1            MPEG-4 part 2 Microsoft variant version 1
 DEV.L. msmpeg4v2            MPEG-4 part 2 Microsoft variant version 2
 DEV.L. msmpeg4v3            MPEG-4 part 2 Microsoft variant version 3 (decoders: msmpeg4_crystalhd msmpeg4 ) (encoders: msmpeg4 )
 D.V..S msrle                Microsoft RLE
 D.V.L. mss1                 MS Screen 1
 D.VIL. mss2                 MS Windows Media Video V9 Screen
 DEV.L. msvideo1             Microsoft Video 1
 D.VI.S mszh                 LCL (LossLess Codec Library) MSZH
 D.V.L. mts2                 MS Expression Encoder Screen
 D.VIL. mvc1                 Silicon Graphics Motion Video Compressor 1
 D.VIL. mvc2                 Silicon Graphics Motion Video Compressor 2
 D.V.L. mxpeg                Mobotix MxPEG video
 D.V.L. nuv                  NuppelVideo/RTJPEG
 D.V.L. paf_video            Amazing Studio Packed Animation File Video
 DEVI.S pam                  PAM (Portable AnyMap) image
 DEVI.S pbm                  PBM (Portable BitMap) image
 DEVI.S pcx                  PC Paintbrush PCX image
 DEVI.S pgm                  PGM (Portable GrayMap) image
 DEVI.S pgmyuv               PGMYUV (Portable GrayMap YUV) image
 D.VIL. pictor               Pictor/PC Paint
 DEV..S png                  PNG (Portable Network Graphics) image
 DEVI.S ppm                  PPM (Portable PixelMap) image
 DEVIL. prores               Apple ProRes (iCodec Pro) (decoders: prores prores_lgpl ) (encoders: prores prores_aw prores_ks )
 D.VIL. ptx                  V.Flash PTX image
 D.VI.S qdraw                Apple QuickDraw
 D.V.L. qpeg                 Q-team QPEG
 DEV..S qtrle                QuickTime Animation (RLE) video
 DEVI.S r10k                 AJA Kona 10-bit RGB Codec
 DEVI.S r210                 Uncompressed RGB 10-bit
 DEVI.S rawvideo             raw video
 D.VIL. rl2                  RL2 video
 DEV.L. roq                  id RoQ video (decoders: roqvideo ) (encoders: roqvideo )
 D.V.L. rpza                 QuickTime video (RPZA)
 DEV.L. rv10                 RealVideo 1.0
 DEV.L. rv20                 RealVideo 2.0
 D.V.L. rv30                 RealVideo 3.0
 D.V.L. rv40                 RealVideo 4.0
 D.V.L. sanm                 LucasArts SANM/SMUSH video
 DEVI.S sgi                  SGI image
 D.VI.S sgirle               SGI RLE 8-bit
 D.V.L. smackvideo           Smacker video (decoders: smackvid )
 D.V.L. smc                  QuickTime Graphics (SMC)
 D.V... smvjpeg              Sigmatel Motion Video
 DEV.LS snow                 Snow
 D.VIL. sp5x                 Sunplus JPEG (SP5X)
 DEVI.S sunrast              Sun Rasterfile image
 DEV.L. svq1                 Sorenson Vector Quantizer 1 / Sorenson Video 1 / SVQ1
 D.V.L. svq3                 Sorenson Vector Quantizer 3 / Sorenson Video 3 / SVQ3
 DEVI.S targa                Truevision Targa image
 D.VI.. targa_y216           Pinnacle TARGA CineWave YUV16
 D.V.L. tdsc                 TDSC
 D.V.L. tgq                  Electronic Arts TGQ video (decoders: eatgq )
 D.V.L. tgv                  Electronic Arts TGV video (decoders: eatgv )
 DEV.L. theora               Theora (encoders: libtheora )
 D.VIL. thp                  Nintendo Gamecube THP video
 D.V.L. tiertexseqvideo      Tiertex Limited SEQ video
 DEVI.S tiff                 TIFF image
 D.VIL. tmv                  8088flex TMV
 D.V.L. tqi                  Electronic Arts TQI video (decoders: eatqi )
 D.V.L. truemotion1          Duck TrueMotion 1.0
 D.V.L. truemotion2          Duck TrueMotion 2.0
 D.V..S tscc                 TechSmith Screen Capture Codec (decoders: camtasia )
 D.V.L. tscc2                TechSmith Screen Codec 2
 D.VIL. txd                  Renderware TXD (TeXture Dictionary) image
 D.V.L. ulti                 IBM UltiMotion (decoders: ultimotion )
 DEVI.S utvideo              Ut Video
 DEVI.S v210                 Uncompressed 4:2:2 10-bit
 D.VI.S v210x                Uncompressed 4:2:2 10-bit
 DEVI.. v308                 Uncompressed packed 4:4:4
 DEVI.. v408                 Uncompressed packed QT 4:4:4:4
 DEVI.S v410                 Uncompressed 4:4:4 10-bit
 D.V.L. vb                   Beam Software VB
 D.VI.S vble                 VBLE Lossless Codec
 D.V.L. vc1                  SMPTE VC-1 (decoders: vc1 vc1_crystalhd vc1_vdpau )
 D.V.L. vc1image             Windows Media Video 9 Image v2
 D.VIL. vcr1                 ATI VCR1
 D.VIL. vixl                 Miro VideoXL (decoders: xl )
 D.V.L. vmdvideo             Sierra VMD video
 D.V..S vmnc                 VMware Screen Codec / VMware Video
 D.V.L. vp3                  On2 VP3
 D.V.L. vp5                  On2 VP5
 D.V.L. vp6                  On2 VP6
 D.V.L. vp6a                 On2 VP6 (Flash version, with alpha channel)
 D.V.L. vp6f                 On2 VP6 (Flash version)
 D.V.L. vp7                  On2 VP7
 DEV.L. vp8                  On2 VP8 (decoders: vp8 libvpx ) (encoders: libvpx )
 DEV.L. vp9                  Google VP9 (decoders: vp9 libvpx-vp9 ) (encoders: libvpx-vp9 )
 DEVILS webp                 WebP (encoders: libwebp )
 DEV.L. wmv1                 Windows Media Video 7
 DEV.L. wmv2                 Windows Media Video 8
 D.V.L. wmv3                 Windows Media Video 9 (decoders: wmv3 wmv3_crystalhd wmv3_vdpau )
 D.V.L. wmv3image            Windows Media Video 9 Image
 D.VIL. wnv1                 Winnov WNV1
 D.V.L. ws_vqa               Westwood Studios VQA (Vector Quantized Animation) video (decoders: vqavideo )
 D.V.L. xan_wc3              Wing Commander III / Xan
 D.V.L. xan_wc4              Wing Commander IV / Xxan
 D.VI.. xbin                 eXtended BINary text
 DEVI.S xbm                  XBM (X BitMap) image
 DEVIL. xface                X-face image
 DEVI.S xwd                  XWD (X Window Dump) image
 DEVI.. y41p                 Uncompressed YUV 4:1:1 12-bit
 D.V.L. yop                  Psygnosis YOP Video
 DEVI.. yuv4                 Uncompressed packed 4:2:0
 D.V..S zerocodec            ZeroCodec Lossless Video
 DEVI.S zlib                 LCL (LossLess Codec Library) ZLIB
 DEV..S zmbv                 Zip Motion Blocks Video
 ..A.L. 4gv                  4GV (Fourth Generation Vocoder)
 D.A.L. 8svx_exp             8SVX exponential
 D.A.L. 8svx_fib             8SVX fibonacci
 DEA.L. aac                  AAC (Advanced Audio Coding) (decoders: aac aac_fixed ) (encoders: aac libvo_aacenc )
 D.A.L. aac_latm             AAC LATM (Advanced Audio Coding LATM syntax)
 DEA.L. ac3                  ATSC A/52A (AC-3) (decoders: ac3 ac3_fixed ) (encoders: ac3 ac3_fixed )
 D.A.L. adpcm_4xm            ADPCM 4X Movie
 DEA.L. adpcm_adx            SEGA CRI ADX ADPCM
 D.A.L. adpcm_afc            ADPCM Nintendo Gamecube AFC
 D.A.L. adpcm_ct             ADPCM Creative Technology
 D.A.L. adpcm_dtk            ADPCM Nintendo Gamecube DTK
 D.A.L. adpcm_ea             ADPCM Electronic Arts
 D.A.L. adpcm_ea_maxis_xa    ADPCM Electronic Arts Maxis CDROM XA
 D.A.L. adpcm_ea_r1          ADPCM Electronic Arts R1
 D.A.L. adpcm_ea_r2          ADPCM Electronic Arts R2
 D.A.L. adpcm_ea_r3          ADPCM Electronic Arts R3
 D.A.L. adpcm_ea_xas         ADPCM Electronic Arts XAS
 DEA.L. adpcm_g722           G.722 ADPCM (decoders: g722 ) (encoders: g722 )
 DEA.L. adpcm_g726           G.726 ADPCM (decoders: g726 ) (encoders: g726 )
 D.A.L. adpcm_g726le         G.726 ADPCM little-endian (decoders: g726le )
 D.A.L. adpcm_ima_amv        ADPCM IMA AMV
 D.A.L. adpcm_ima_apc        ADPCM IMA CRYO APC
 D.A.L. adpcm_ima_dk3        ADPCM IMA Duck DK3
 D.A.L. adpcm_ima_dk4        ADPCM IMA Duck DK4
 D.A.L. adpcm_ima_ea_eacs    ADPCM IMA Electronic Arts EACS
 D.A.L. adpcm_ima_ea_sead    ADPCM IMA Electronic Arts SEAD
 D.A.L. adpcm_ima_iss        ADPCM IMA Funcom ISS
 D.A.L. adpcm_ima_oki        ADPCM IMA Dialogic OKI
 DEA.L. adpcm_ima_qt         ADPCM IMA QuickTime
 D.A.L. adpcm_ima_rad        ADPCM IMA Radical
 D.A.L. adpcm_ima_smjpeg     ADPCM IMA Loki SDL MJPEG
 DEA.L. adpcm_ima_wav        ADPCM IMA WAV
 D.A.L. adpcm_ima_ws         ADPCM IMA Westwood
 DEA.L. adpcm_ms             ADPCM Microsoft
 D.A.L. adpcm_sbpro_2        ADPCM Sound Blaster Pro 2-bit
 D.A.L. adpcm_sbpro_3        ADPCM Sound Blaster Pro 2.6-bit
 D.A.L. adpcm_sbpro_4        ADPCM Sound Blaster Pro 4-bit
 DEA.L. adpcm_swf            ADPCM Shockwave Flash
 D.A.L. adpcm_thp            ADPCM Nintendo THP
 D.A.L. adpcm_thp_le         ADPCM Nintendo THP (Little-Endian)
 D.A.L. adpcm_vima           LucasArts VIMA audio (decoders: adpcm_vima vima )
 D.A.L. adpcm_xa             ADPCM CDROM XA
 DEA.L. adpcm_yamaha         ADPCM Yamaha
 DEA..S alac                 ALAC (Apple Lossless Audio Codec)
 DEA.L. amr_nb               AMR-NB (Adaptive Multi-Rate NarrowBand) (decoders: amrnb libopencore_amrnb ) (encoders: libopencore_amrnb )
 DEA.L. amr_wb               AMR-WB (Adaptive Multi-Rate WideBand) (decoders: amrwb libopencore_amrwb ) (encoders: libvo_amrwbenc )
 D.A..S ape                  Monkey's Audio
 D.A.L. atrac1               ATRAC1 (Adaptive TRansform Acoustic Coding)
 D.A.L. atrac3               ATRAC3 (Adaptive TRansform Acoustic Coding 3)
 D.A.L. atrac3p              ATRAC3+ (Adaptive TRansform Acoustic Coding 3+) (decoders: atrac3plus )
 D.A.L. avc                  On2 Audio for Video Codec (decoders: on2avc )
 D.A.L. binkaudio_dct        Bink Audio (DCT)
 D.A.L. binkaudio_rdft       Bink Audio (RDFT)
 D.A.L. bmv_audio            Discworld II BMV audio
 ..A.L. celt                 Constrained Energy Lapped Transform (CELT)
 DEA.L. comfortnoise         RFC 3389 Comfort Noise
 D.A.L. cook                 Cook / Cooker / Gecko (RealAudio G2)
 D.A.L. dsd_lsbf             DSD (Direct Stream Digital), least significant bit first
 D.A.L. dsd_lsbf_planar      DSD (Direct Stream Digital), least significant bit first, planar
 D.A.L. dsd_msbf             DSD (Direct Stream Digital), most significant bit first
 D.A.L. dsd_msbf_planar      DSD (Direct Stream Digital), most significant bit first, planar
 D.A.L. dsicinaudio          Delphine Software International CIN audio
 D.A.L. dss_sp               Digital Speech Standard - Standard Play mode (DSS SP)
 DEA.LS dts                  DCA (DTS Coherent Acoustics) (decoders: dca ) (encoders: dca )
 ..A.L. dvaudio              DV audio
 DEA.L. eac3                 ATSC A/52B (AC-3, E-AC-3)
 D.A.L. evrc                 EVRC (Enhanced Variable Rate Codec)
 DEA..S flac                 FLAC (Free Lossless Audio Codec)
 DEA.L. g723_1               G.723.1
 D.A.L. g729                 G.729
 DEA.L. gsm                  GSM (decoders: gsm libgsm ) (encoders: libgsm )
 DEA.L. gsm_ms               GSM Microsoft variant (decoders: gsm_ms libgsm_ms ) (encoders: libgsm_ms )
 D.A.L. iac                  IAC (Indeo Audio Coder)
 ..A.L. ilbc                 iLBC (Internet Low Bitrate Codec)
 D.A.L. imc                  IMC (Intel Music Coder)
 D.A.L. interplay_dpcm       DPCM Interplay
 D.A.L. mace3                MACE (Macintosh Audio Compression/Expansion) 3:1
 D.A.L. mace6                MACE (Macintosh Audio Compression/Expansion) 6:1
 D.A.L. metasound            Voxware MetaSound
 D.A..S mlp                  MLP (Meridian Lossless Packing)
 D.A.L. mp1                  MP1 (MPEG audio layer 1) (decoders: mp1 mp1float )
 DEA.L. mp2                  MP2 (MPEG audio layer 2) (decoders: mp2 mp2float ) (encoders: mp2 mp2fixed libtwolame )
 DEA.L. mp3                  MP3 (MPEG audio layer 3) (decoders: mp3 mp3float ) (encoders: libmp3lame libshine )
 D.A.L. mp3adu               ADU (Application Data Unit) MP3 (MPEG audio layer 3) (decoders: mp3adu mp3adufloat )
 D.A.L. mp3on4               MP3onMP4 (decoders: mp3on4 mp3on4float )
 D.A..S mp4als               MPEG-4 Audio Lossless Coding (ALS) (decoders: als )
 D.A.L. musepack7            Musepack SV7 (decoders: mpc7 )
 D.A.L. musepack8            Musepack SV8 (decoders: mpc8 )
 DEA.L. nellymoser           Nellymoser Asao
 DEA.L. opus                 Opus (Opus Interactive Audio Codec) (decoders: opus libopus ) (encoders: libopus )
 D.A.L. paf_audio            Amazing Studio Packed Animation File Audio
 DEA.L. pcm_alaw             PCM A-law / G.711 A-law
 D.A..S pcm_bluray           PCM signed 16|20|24-bit big-endian for Blu-ray media
 D.A..S pcm_dvd              PCM signed 20|24-bit big-endian
 DEA..S pcm_f32be            PCM 32-bit floating point big-endian
 DEA..S pcm_f32le            PCM 32-bit floating point little-endian
 DEA..S pcm_f64be            PCM 64-bit floating point big-endian
 DEA..S pcm_f64le            PCM 64-bit floating point little-endian
 D.A..S pcm_lxf              PCM signed 20-bit little-endian planar
 DEA.L. pcm_mulaw            PCM mu-law / G.711 mu-law
 DEA..S pcm_s16be            PCM signed 16-bit big-endian
 DEA..S pcm_s16be_planar     PCM signed 16-bit big-endian planar
 DEA..S pcm_s16le            PCM signed 16-bit little-endian
 DEA..S pcm_s16le_planar     PCM signed 16-bit little-endian planar
 DEA..S pcm_s24be            PCM signed 24-bit big-endian
 DEA..S pcm_s24daud          PCM D-Cinema audio signed 24-bit
 DEA..S pcm_s24le            PCM signed 24-bit little-endian
 DEA..S pcm_s24le_planar     PCM signed 24-bit little-endian planar
 DEA..S pcm_s32be            PCM signed 32-bit big-endian
 DEA..S pcm_s32le            PCM signed 32-bit little-endian
 DEA..S pcm_s32le_planar     PCM signed 32-bit little-endian planar
 DEA..S pcm_s8               PCM signed 8-bit
 DEA..S pcm_s8_planar        PCM signed 8-bit planar
 DEA..S pcm_u16be            PCM unsigned 16-bit big-endian
 DEA..S pcm_u16le            PCM unsigned 16-bit little-endian
 DEA..S pcm_u24be            PCM unsigned 24-bit big-endian
 DEA..S pcm_u24le            PCM unsigned 24-bit little-endian
 DEA..S pcm_u32be            PCM unsigned 32-bit big-endian
 DEA..S pcm_u32le            PCM unsigned 32-bit little-endian
 DEA..S pcm_u8               PCM unsigned 8-bit
 D.A.L. pcm_zork             PCM Zork
 D.A.L. qcelp                QCELP / PureVoice
 D.A.L. qdm2                 QDesign Music Codec 2
 ..A.L. qdmc                 QDesign Music
 DEA.L. ra_144               RealAudio 1.0 (14.4K) (decoders: real_144 ) (encoders: real_144 )
 D.A.L. ra_288               RealAudio 2.0 (28.8K) (decoders: real_288 )
 D.A..S ralf                 RealAudio Lossless
 DEA.L. roq_dpcm             DPCM id RoQ
 DEA..S s302m                SMPTE 302M
 D.A..S shorten              Shorten
 D.A.L. sipr                 RealAudio SIPR / ACELP.NET
 D.A.L. smackaudio           Smacker audio (decoders: smackaud )
 ..A.L. smv                  SMV (Selectable Mode Vocoder)
 D.A.L. sol_dpcm             DPCM Sol
 DEA... sonic                Sonic
 .EA... sonicls              Sonic lossless
 DEA.L. speex                Speex (decoders: libspeex ) (encoders: libspeex )
 D.A..S tak                  TAK (Tom's lossless Audio Kompressor)
 D.A..S truehd               TrueHD
 D.A.L. truespeech           DSP Group TrueSpeech
 DEA..S tta                  TTA (True Audio)
 D.A.L. twinvq               VQF TwinVQ
 D.A.L. vima                 LucasArts VIMA audio (deprecated id) (decoders: adpcm_vima vima )
 D.A.L. vmdaudio             Sierra VMD audio
 DEA.L. vorbis               Vorbis (decoders: vorbis libvorbis ) (encoders: vorbis libvorbis )
 ..A.L. voxware              Voxware RT29 Metasound
 D.A... wavesynth            Wave synthesis pseudo-codec
 DEA.LS wavpack              WavPack (encoders: wavpack libwavpack )
 D.A.L. westwood_snd1        Westwood Audio (SND1) (decoders: ws_snd1 )
 D.A..S wmalossless          Windows Media Audio Lossless
 D.A.L. wmapro               Windows Media Audio 9 Professional
 DEA.L. wmav1                Windows Media Audio 1
 DEA.L. wmav2                Windows Media Audio 2
 D.A.L. wmavoice             Windows Media Audio Voice
 D.A.L. xan_dpcm             DPCM Xan
 ..D... bin_data             binary data
 ..D... dvd_nav_packet       DVD Nav packet
 ..D... klv                  SMPTE 336M Key-Length-Value (KLV) metadata
 ..D... otf                  OpenType font
 ..D... timed_id3            timed ID3 metadata
 ..D... ttf                  TrueType font
 DES... ass                  ASS (Advanced SSA) subtitle
 DES... dvb_subtitle         DVB subtitles (decoders: dvbsub ) (encoders: dvbsub )
 D.S... dvb_teletext         DVB teletext (decoders: libzvbi_teletextdec )
 DES... dvd_subtitle         DVD subtitles (decoders: dvdsub ) (encoders: dvdsub )
 D.S... eia_608              EIA-608 closed captions (decoders: cc_dec )
 D.S... hdmv_pgs_subtitle    HDMV Presentation Graphic Stream subtitles (decoders: pgssub )
 ..S... hdmv_text_subtitle   HDMV Text subtitle
 D.S... jacosub              JACOsub subtitle
 D.S... microdvd             MicroDVD subtitle
 DES... mov_text             MOV text
 D.S... mpl2                 MPL2 subtitle
 D.S... pjs                  PJS (Phoenix Japanimation Society) subtitle
 D.S... realtext             RealText subtitle
 D.S... sami                 SAMI subtitle
 ..S... srt                  SubRip subtitle with embedded timing
 DES... ssa                  SSA (SubStation Alpha) subtitle
 D.S... stl                  Spruce subtitle format
 DES... subrip               SubRip subtitle (decoders: srt subrip ) (encoders: srt subrip )
 D.S... subviewer            SubViewer subtitle
 D.S... subviewer1           SubViewer v1 subtitle
 D.S... text                 raw UTF-8 text
 D.S... vplayer              VPlayer subtitle
 DES... webvtt               WebVTT subtitle
 DES... xsub                 XSUB
```

AAC Codecs, as run through grep:

```
 DEA.L. aac                  AAC (Advanced Audio Coding) (decoders: aac aac_fixed ) (encoders: aac libvo_aacenc )
 D.A.L. aac_latm             AAC LATM (Advanced Audio Coding LATM syntax)
```

So, I need to support any dot pattern, but include E and A.

---

### Post by Yellow Pasque on 2017-05-12
Sorry, but I don't think I have anything to contribute beyond what I've already given.

---

### Post by Yellow Pasque on 2017-05-21
I have no idea why the AAC patch didn't work for you (worked for me). It may just be easier to search for "encoders: aac" if the regex causes you problems.

---

### Post by rdragonrydr on 2017-05-25
I got it working. It has now been submitted at the reviewboard. Thanks for putting up with me, and you'll be happy to know that there wasn't a problem with the regex after all. Just one more silly thing on my part-- I did not purge the support libs for amarok before testing, so it would seem that it still ran the old check when I tested it.

I couldn't get the HeAAC one to work. I am sorry, but I can't figure out why. It looks exactly like the other, functioning ones.

---

