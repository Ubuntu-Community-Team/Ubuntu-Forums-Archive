---
title: "Volume normalization"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by Paul86fxr on 2008-02-26
Is there a plugin or package that will normalize the volume of MP3's when recording them to an MP3 player or CD, by that I mean, songs of different recorded volume levels are all made equal prior to burning or transferring  to a MP3, most recorder software comes with this burn option but my machine refuses to run windows. Any ideas out there?

---

### Post by JoeLinux117 on 2008-02-26
Have a look at "mp3gain".  It should be in the repositories.  It's excellent, I use it all the time for burning CDs, and there is no loss in quality, as it doesn't re-encode the mp3s.


--JoeLinux
[Learn About Linux - A World Without Windows]("http://www.learnaboutlinux.net")

---

### Post by Paul86fxr on 2008-02-26
looks good Joe, I just dont know how to install it, a hint or two might help, i'm not good with 'tar.gz' packages yet.

---

### Post by wheelie77 on 2008-03-09
Hey,

I am also interested in mp3gain and its use. I installed it using: 

> sudo apt-get install mp3gian

This seemed to work ok, and i have it installed but there is a problem. I was hoping that there would be a GUI for ease of use but there dosent seem to be one installed from that command. Next I thought i would just do it from the shell but that is also a pain the it ***. I though it would be as simple as listing all file names and applying the mp3gain to them in turn:

> for name in `find ~/Music/ -type f`; do mp3gain -r $name; done

This did not work because of white-space in file names etc...

It would be nice if there was just a recursive flag on mp3gain so I could just do my entire library in one go???

Hopefully the answer is yes :P

Cheers Dave

---

### Post by wheelie77 on 2008-03-09
Hey Paul86fxr,

I just did a little more searching and found a command that simplifies running mp3gain from the terminal:

> find /home/Music -type f -iname '*.mp3' -print0 | xargs -0 mp3gain -r -k

*'What it does is, it finds all files (type -f) in the present directory (.) with a name that ends in &#8220;.mp3&#8243; and creates a list of the same. The output of this find command is then piped to the mp3gain program. The options that I ended up using for mp3gain, -r and -k dictate that the calculated track gain will be applied automatically to normalize the volume, and that files should be protected against &#8220;clipping&#8221; by lowering the applied gain if the required gain seems likely to clip the sound. Concoct your own recipe by referring to the man page for mp3gain.'*

This might help you on your way but I have to thank [Carthik]("http://ubuntu.wordpress.com/category/packages/"), for the enhanced command and simple description.

PS: remember that if you have a large collection of music files it will take a while to finish. I have 1300 and it took about 1 hour.

Cheers Dave

---

### Post by vanadium on 2008-03-16
It can be more simple:

find /home/Music -iname '*.mp3' -execdir mp3gain -r -k "{}" \;

---

### Post by Giantics on 2008-03-28
Hello

> **wheelie77 said:**
> I was hoping that there would be a GUI for ease of use but there dosent seem to be one installed from that command. 

Cause I was also missing such a GUI, I started the project easyMP3Gain, a few months ago.

[http://sourceforge.net/projects/easymp3gain/]("http://sourceforge.net/projects/easymp3gain/")
Please have a look at it :-)
The deb-Package is created for (K)Ubuntu Gutsy.

Giantics

---

### Post by AustinMatherne on 2008-04-10
> **Giantics said:**
> Hello



Cause I was also missing such a GUI, I started the project easyMP3Gain, a few months ago.

[http://sourceforge.net/projects/easymp3gain/]("http://sourceforge.net/projects/easymp3gain/")
Please have a look at it :-)
The deb-Package is created for (K)Ubuntu Gutsy.

Giantics

Do you plain to support oggain in the future?

~ Austin

---

### Post by Giantics on 2008-04-13
> **AustinMatherne said:**
> Do you plain to support oggain in the future?

~ Austin

Yes, I'm already working on it. I think it will take a few more months.

Giantics

---

### Post by Anthony M on 2008-04-23
How do i install this on a 64-bit Ubuntu machine?

---

### Post by Giantics on 2008-04-26
You have two possibilities to install it on a 64bit-machine.

a) sudo dpkg --force-architecture -i thepackage.deb
b) download the tar.gz package of easymp3gain and unpack it manually.

Thomas

---

### Post by Squiffy on 2008-04-29
I've tried option A but while the program kicks up fine, when I try to add a file/folder it crashes out. ah well, back to the command line for me!

---

### Post by Giantics on 2008-05-02
Could you please run easymp3gain by command line, and post the output here after the crash?
Perhaps I can fix the problem.

---

### Post by teemac on 2008-06-01
Giantics - Thank you so very much for your frontend to mp3gain.

I have been using it in WinXP for years and missed it badly since changing over to Kubuntu64 last year.

Just found this thread and thought I would give it a go.

Works perfect - thanks mate - your work very much appreciated.

My current system:

Q6600 with Kubuntu64 v8.04 2gb ram.

How I got it to work:

Simply downloaded 'easymp3gain_0.3.0_gtk2_i386.tar.gz' from sourceforge and unpacked it to a folder in my home.

Click on file 'easymp3gain'

It just works - that simple. \\:D/

Thanks again - really a lot easier than jumping into VBox XP every time I needed mp3gain.

---

### Post by Giantics on 2008-06-01
Hi teemac,

thank you very much for your commendation.
Nice to hear that people are using easyMP3Gain and that it works :-)

Til now the binary was just supposed to run on 64bit-systems. Now I know it!

---

### Post by Joe on 2008-06-07
Giantics, first thanks for the GUI!  Have been looking for something like this for a long time.  Now a couple questions:

1) Am I correct in assuming that "Analysis" applies the replaygain info only to the tags while "Modify Gain" means that it modifies the track itself?

2) Is it possible to scan and prevent clipping at this time?

Also, one suggestion.  Perhaps it's better to use aacgain instead of mp3gain since aacgain is able to replaygain both aac files and mp3 files.

---

### Post by ace2269 on 2008-06-07
Hello, I have a great sony viao laptop for sale right now just wanted to let you guys know if anyone needed one its only at 338.00 right now and has tons of software with it.  Games recovery dish everything is in working condition and mint condition.  :) Great Laptop.[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWAX:IT&item=320260029021](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWAX:IT&item=320260029021)

Thats the link just copy and paste it.  Will take ya right theire to check it out.           Tech geek Mike:):KS

---

### Post by Giantics on 2008-06-08
Thanks Joe,

1) Yes, that's correct. "Analysis" just scans the files and writes the info-tags. "Modify Gain" modifies the volume (it writes the volume-tag)!
 
 2) After analyzing the files, reduce the value of the target-volume, until every file displays a "no" in the clip-column. Perhaps I'll include a "max-no-clip-gain" in the future.
 
I didn't know aacgain til now. Thanks for that tip!
I'm going to have a look at it.

---

