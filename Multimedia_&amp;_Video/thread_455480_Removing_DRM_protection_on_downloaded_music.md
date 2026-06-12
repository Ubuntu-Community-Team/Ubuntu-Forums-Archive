---
title: "Removing DRM protection on downloaded music"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by t2000kw on 2007-05-26
Is there an easy approach to doing in Linux what Fair Use for Windows Media does in Windows to remove the digital rights management to allow copying a protected file to an unprotected MP3 format so it's more portable (as in using a USB drive to store some)?

---

### Post by jubxie on 2007-05-26
not sure if this is what your looking for but there is a program called tunebite that uses the sound card to record drm'd music while it is playing. the obvious problem with this is that you have to be playing the drm'd music. this is a windows solution to removing drm and it worked well for me with rhapsody songs. this is not perfect, but untll un-drm'd music is widely available, this could get all your purchaced, drm'd music over to linux. also creates .ogg. costs $20 us i think.

---

### Post by kyleabaker on 2007-10-07
Is there a more efficient method to removing DRM protection in Linux? This sounds like it could be a long process for larger collections. I saw where some people attempted to run some programs through wine, but something designed for Unix based systems that can just strip the protection out and reprocess it would be ideal. I still have several songs that I got before I switched to Ubuntu from Windows and am unable to easily play them. Hopefully we can find a good work around.

Anyone have any suggestions (since it has been several months since this was last brought up in here)?

---

### Post by t2000kw on 2007-10-07
One way of doing this, and it's probably no quicker than the last suggestion, is to make audio CD files fromt he DRM MP3s, then convert those to MP3s, which then wouldn't have DRM.

You would lose some fidelity in the process, I think.

---

### Post by t2000kw on 2007-10-11
This looks like a Windows program. It's strange that it has a file extension of .com.exe and looks a bit suspicious, but it seems to get some good reviews. 

Does this run under Wine or Crossover Office or does a person have to have Windows on his/her PC to use it?

Also, how well does it work with video files (one of the versions says it works with video to remove DRM)?

---

### Post by telnet110 on 2007-10-18
Yes this is a windows software. I have concluded that the easiest way so far to convert your protected files is emulating a windows software. Especially on large libraries. I am using [Tunebite]("http://audials.com/en/remove_drm/index.html") because of it's accelerated conversion process(up to 4x real-time). And it also does respectable work with video files too, depending on how powerfull your PC is.

Btw. this Tunecab it's a lot of bs in my opinion, but every1 is entitled to an opinion, right ?

---

### Post by zmjjmz on 2007-10-21
Let's see...
I've tried

Noteburner, Soundtaxi/Tunecab (they're the same thing...), and Protected Music Converter.
I can't do the CD thing because I don't have any working install of Mac or Windows with iTunes...
There must be a better way to do this...

---

### Post by Auslegung on 2007-10-22
You originally said you want to easily listen to DRMed music, and while I know you would much rather remove the DRM (wouldn't we all), Songbird provides a way to play all your music, DRMed or not.  Go to <http://www.songbirdnest.com/>.  It's still in a developer preview, but as you will probably see it has immense potential.

---

### Post by cogadh on 2007-10-22
I didn't see anything that said it could handle DRM music on Linux, but I could have just missed it. Are you sure it can do that?

EDIT - NVM, I found my answer in the support section, it can't do DRM on Linux:

*Can I play my purchased music from services such as the new Napster, MusicMatch, MusicNow, or BuyMusic.com with Songbird?*
Songbird can play any popular music file format that is not DRM'ed. We will also be able play Windows Media DRM on PCs soon (but not on Macs or Linux). We are looking into legal ways to play music from the iTunes Music Store that has FairPlay DRM.

---

### Post by t2000kw on 2007-10-22
I don't see anything in the Songbird manual about playing DRM music. Actually, I don't see much in the 4 page manual at all, but I did check it out. However, the web site mentions that it can play songs from iTunes or Yahoo! Unlimited. Does this mean that it will only play the ones that are DRM-free from those sites? With the absence of a statement that it will actually play music with DRM on it, the logical assumption is that it won't, and it appears that mention of playing songs from these sources are relating to the ones offered without DRM on those sites.

If it is true that it will actually allow you to take a DRM MP3 and play it on your PC, laptop, and MP3 player, all without having to download a copy of the song for each, they are doing themselves a disservice by not explicitly stating so. 

It does look like they are at the very beginnings with their product, though, so maybe they need to sort a lot out before it's worth their time to make the web site advertise their product better.

---

### Post by telnet110 on 2007-10-23
I don't know why they even presented it as an option, while it is not working yet...

---

### Post by airtonix on 2007-10-27
someone told me if you open the song in a hex editor..and remove the last/first 4 bytes, the drm becomes void...and its just a normal mp3 then.


but what would i know.

---

### Post by t2000kw on 2007-10-27
if it were that easy, it would be all over the Internet, wouldn't it? 

There is probably something attached throughout the music file that gets skipped over when it's properly decoded but renders it useless otherwise.

---

### Post by KatriS on 2008-02-22
I use [Tunebite]("http://audials.com/en/audials_one/format_converter/index.html") for removing that DRM protection and also for converting video and audio files...It is OK for me, easy to use and useful for people who's passion is music......:guitar:

---

