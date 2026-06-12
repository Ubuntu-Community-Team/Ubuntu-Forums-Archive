---
title: "How to create a video dvd from a .mp4 file?"
date: 2015-01-18
forum: Multimedia Software
---

### Post by michael-piziak on 2015-01-18
How can I create a video dvd (or cd) from an .mp4 file?

Hopefully this can be done with software already on my 12.04 lts system.

---

### Post by David D. on 2015-01-19
I use DeVeDe to create DVDs from video files such as .mp4.  The software is in the respositories/Ubuntu Software Center.

---

### Post by michael-piziak on 2015-01-19
Thanks,

I will download that program.
I'm curious though - will Brasero disk burner not do it that is already installed ?

---

### Post by Rob Sayer on 2015-01-19
Don't just download it from some site.  Use synaptic or software center.

A burning program like brasero usually won't work.  DVD players are very fussy about what video formats they'll accept.  The .mp4 extension tells you nothing about the format actually.  It's a container, not a format, and since mp4 is a very versatile container it could be anything.

But nowadays it's usually h.264 video, which dvd players don't recognize AFAIK.  It usually has to be either standard DVD compliant mpeg-2 or divx/xvid.

---

### Post by michael-piziak on 2015-01-19
Brasero has an option for a video project to make a DVD - ?

Anyways, I need to get some DVD's to do this.  My CD's don't have enough space on them.

---

### Post by SeijiSensei on 2015-01-19
I'd bet that Brasero option is designed to put files onto a DVD.

A DVD that plays in a DVD player has a very restrictive format.  The video has to be encoded in MPEG2, for instance.  Just copying an MP4 file to the DVD won't work; it will only play on a computer.

---

### Post by michael-piziak on 2015-01-19
When I get some blank DVD's I'll give Brasero a try.  If not, I'll use the recommended program from the Software Center.

Brasero does "appear" to have many options including make a video DVD.  See attached screenshot.

---

### Post by michael-piziak on 2015-01-19
Update:  I downloaded a very short movie and am now attempting to use Brasero to make a video disk of it (on a CD).  It told me it needed to fetch "vcdimager," so I let it do that.

Right now it's converting video file to "mpeg2"

I'll report back if the final disk works in a dvd player.

update:  Brasero wouldn't do anything, even with the "vcdimager" installed.  It just sat there at 2mib.

I'm now using DeVeDe to try to make a CD video disk.   Will a CD video disk work in a DVD player?

---

### Post by yancek on 2015-01-19
> Will a CD video disk work in a DVD player? 		

I can't think of any reason why not.  You can read a standard CD from a DVD player.  Of course, the reverse won't work.

---

### Post by michael-piziak on 2015-01-19
I don't know what the problem is, but DeVEDe kept coming up with an error when attempting to make even a small movie into a video cd.

---

### Post by yancek on 2015-01-19
Someone might be able to help if you indicated what the error was!

---

### Post by michael-piziak on 2015-01-19
I'll give it another go tomorrow and report back with the specific error message.  I am away from the computer now.

---

### Post by andrew.46 on 2015-01-19
Perhaps this older post might help:

[http://ubuntuforums.org/showthread.php?t=2150361&p=12674818&viewfull=1#post12674818](http://ubuntuforums.org/showthread.php?t=2150361&p=12674818&viewfull=1#post12674818)

---

### Post by SeijiSensei on 2015-01-20
Have DeVeDe make an ISO image first and see if you can play that before burning.

---

### Post by michael-piziak on 2015-01-20
I attempted to create a video cd using3 options in DeVeDE.  Below are the error messages I received witheach option:


VCD attempt:  Conversion failed.  Itseems a bug of MenCoder


SVCD attempt:  Please select anotherimage &#8230;     Error getting information forfile'/home/michael/movie/movie.iso': No such file or directory


CVD attempt:  Please select anotherimage.  Error getting information forfile'/home/michael/movie/movie.iso': No such file or directory

---

### Post by michael-piziak on 2015-01-20
> **SeijiSensei said:**
> Have DeVeDe make an ISO image first and see if you can play that before burning.

I have the advanced option selected to create an ISO as seen in my attached screen shot; however, at the end of the process, there is no ISO image in the movie folder - usually a .bin or .cue file is in there), and the error message generally points to the fact that no movie.iso file could be found.

---

### Post by michael-piziak on 2015-01-20
I used Brasero to make ISO images of 2 different mp4 movies and save to the desktop.  I then tried to get DeVeDe to make a CD movie out of either iso.  The following message appeared each time:

"File seems to be an audio file."     and thus DeVeDe would not proceed further.

---

### Post by michael-piziak on 2015-01-20
> **andrew.46 said:**
> Perhaps this older post might help:

[http://ubuntuforums.org/showthread.php?t=2150361&p=12674818&viewfull=1#post12674818](http://ubuntuforums.org/showthread.php?t=2150361&p=12674818&viewfull=1#post12674818)


I read that post and I'm trying "DVD Styler" in that post also.  Thanks.

Update:  During the process of using DVD Styler, it will prompt "file contains PAL, do you want to convert DVD to Pal too ?"    I clicked no.  We'll see if this works.

Update:  DVD Styler won't write to a CD.  So I'm going to have to get some blank DVD's before I can try it again.

---

### Post by mc4man on 2015-01-20
Regarding devede - 
For vcd it creates a bin & cue, not an .iso. For DVD_VIDEO it would create an .iso
Unless you have a small tv. can't see why you'd want vcd which is 352x240 resolution. svcd is a bit better, 480x480,  but many dvd players don't support svcd 
So DVD_VIDEO is a better option though these days any run of the mill blu-ray player will support .mp4 files as is. Here I just put them on a usb stick & done.

---

### Post by michael-piziak on 2015-01-20
I had not considered a USB stick to watch the movies on.  That would be less expensive too.

I'll search for how to do this and start a new thread if I can't figure this out.

---

### Post by vinnywright on 2015-01-20
did you install DeVeDe from your package manager?

DeVeDe has always worked @hear for making a DVD ,,,,,,,vcd or svcd ,,,will depend on the player.

your errors mention mencoder go to edit preferences in DeVeDe and select avconv for the encoder and try for a DVD.iso ,,, then you can burn that to a DVD with Brasero.

VINNY

---

### Post by SeijiSensei on 2015-01-21
Putting the files on a stick works if the TV supports the codecs and containers used.  Usually MP4 or AVI is a better bet for compatibility than MKV.  Most TVs are happy with XviD in the AVI container, or H.264 in the MP4 container.  Less-common codecs like Ogg Vorbis or FLAC may also have limited support.  I did a couple of tests with a Samsung "SMART" TV.  I could play an MP4 with H.264 as the video codec and AAC for the audio.  A more demanding file in H.264 with 10-bit color and FLAC audio would not play at all.  Another with H.264+Ogg would play the video but could not decode the audio.  If you can choose your output format, I'd start with H.264 and AAC in the .mp4 container.

Update: My LG 55LN5710 played the file with the Ogg audio; it was in the Matroska (MKV) container, too.  However both TVs refused to play an audio track encoded with FLAC.

---

### Post by michael-piziak on 2015-01-21
Thanks everyone for the help.  I've decided to take a different route and use a USB flash drive to watch movies on the television.

---

