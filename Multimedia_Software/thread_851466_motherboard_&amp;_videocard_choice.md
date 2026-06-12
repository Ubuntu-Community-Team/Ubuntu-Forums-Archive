---
title: "motherboard &amp; videocard choice"
date: 2008-07-06
forum: Multimedia Software
---

### Post by mgtech on 2008-07-06
FYI: I am a newbie when it comes to linux. I am familiar with hardware and the many faults of windows, not linux/ open source software.:(

I am contemplating the possibility of the assembly of a computer to run 8.04.1 on. Its main purpose will be media and consequently media storage. I was hoping that those familiar with ubuntu for this purpose could give some advice. Thanks in advance.

On Windows many video assignments are going to be given to the video card rather soon, encoding etc. - CUDA etc. Is this in the future for  Ubuntu? If so, how soon, and would it therefore be worth it to purchase a videocard even though I won't be gaming on it. 

If not then what motherboard chipset should I purchase based on the fact that although intel most certainly has faster cpus than amd, but the amd 780g and upcoming 780gx most certainly have better integrated graphics. How important are the onboard chipsets to the performance of a ubuntu based machine. Would it affect any video converting, experience etc.?

That being said I am aware that historically ATI now part of AMD has shown rather poor support for linux in general, but I read somewhere that they're trying to fix that with the 4800 release. Any progress? Does this apply to their chipsets as well. If so would I be better off with intel integrated graphics - nvidia hasn't been doing much integrated lately, however they produce fine gpus.I am just not confident in my newbiness(if that is a word) to be messing with drivers in linux.

Memory is also important to the experience of a computer and I would like to know how linux handles memory. Do you need as much as the garbage windows to experience smooth usage. also are there crazy memory barriers in the number of gb that you can have- ie. 3.5 for 32bit and 12 for 64bit(windows) 

On the storage note - what hard drive would do well to store movies. I am thinking about 1tb hds, but the price seems to be higher per gb. Perhaps a few wd 640 gb on newegg $95. Random q: Is SCSI still any faster than a more conventional SATA 3.0gb/sec. set-up. If so how much? It is probably not worth the money though because I need mass storage and I don't have that kind of money to throw into expensive hds and a controller card.

I know that this is farther off topic, but since I will be using this computer for media what media player should I use. I was wondering if there was a media player that had a library similar to that of wmp. Just a novel idea, or is there something better? I am completeley uninformed in this area. What is with all of this messing with directories and codecs stuff. What would be a good linux video converter and a program to open .rar files? HJSplit is available for linux.

Are all of the distros available at distrowatch.com live cds and then install?

Feel free to pick apart anything that you see fit and answer any questions hat you are knowledgeable in. Thanks again for informing myself, a beginner.:)

---

### Post by mgtech on 2008-07-06
help a newbie.
I wish that I was cool enough to have someone reply to my thread, just an idea.

---

### Post by s3a on 2008-07-07
_Video editing:_ intergrated graphics won't be as good as normal graphics for video editing. Cinelerra is the best linux video editor there is and it doesn't have high hardware demands as does Adobe Premiere Pro for Windows.

_.rar files:_
Do you want to create .rar files or only be able to extract them? I suggest you use another format such as **.zip** or **.7z**. To install a fully free as in freedom .rar file extracter, open your terminal (Applications-->Accessories-->Terminal) and type in "**sudo apt-get install unrar-free**." Right clicking on .rar files and selecting to extract will extract those files.

_Memory barriers:_ Memory barriers are in all 32-bit operating systems, including Windows and Linux.

_Choice of video card:_ Choose your videocard and then check the Ubuntu wiki to see if other Ubuntu users had problems with it or not.

_Distrowatch comment:_ Many linux distributions use live cds, however, I obviously recommend Ubuntu over any other distro. My opinion may be a little biased but, you are asking this in **_ubuntu**forums_ afterall. Don't start becoming distro obssesive like many people here, they keep switching operating systems every so often. Just stay with Ubuntu and keep upgrading and enjoy using your computer over installing operating systems day and night.

_Recommended hardware:_ I recommend minimum 512 MB of RAM but I guess you're going to buy a lot of RAM therefore, go with 64-bit Ubuntu. Don't worry the 64-bit version has good support especially these days and many 32-bit apps can be installed in the 64-bit version of Ubuntu if you happen to encounter an application that is solely for 32-bit Ubuntu.

_Windows Media Player alternatives:_ Totem and my prefered application (Rhythmbox) are pre-installed in Ubuntu for what Windows Media Player would do and if you ever need proprietary format support (such as .mp3 files), you can always obtain them from the repositories.
__________________________________________________________________
If you have any more questions, ask.

---

