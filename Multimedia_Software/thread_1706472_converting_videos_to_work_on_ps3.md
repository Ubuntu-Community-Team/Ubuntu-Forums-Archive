---
title: "converting videos to work on ps3"
date: 2011-03-13
forum: Multimedia Software
---

### Post by xinate_dogix on 2011-03-13
im going to apologize in advance since im sure there is an answer to my question already in the forums. but i have been searching for several hours and am now totally confused. i really am not familiar with anything audio/video so please just be patient with me.

heres my problem. im setting up an external hard drive for movies and music to connect to my ps3. the majority of the movies work just fine (they are in mpeg format). but over half of them are HD and take up somewhere in the range of 5 to 8 gigs. since ps3 only supports fat32 externally i can only have file sizes up to 4 gigs. so i need to split the oversized videos into two parts, but i dont know how to do that. ive tried using avidemux (which is a pretty cool program and actually taught me alot) but i cant seem to get a correct format that will work with the ps3. playstations website listed several formats the ps3 is supposed to recognize but none seamed to work for me (maybe i did it wrong though). can anyone give me a step by step explanation to get where i want? or at least point me in the right direction?

---

### Post by coffeecat on 2011-03-14
Yes, this is a real problem with the PS3. Why it doesn't support NTFS is beyond me.

One answer might be to render your mpegs into MP4's with Handbrake. Handbrake can use the H264 video encoder which gives much lower file sizes than (most?) other encoders. You need to enable a PPA to install handbrake. See here:

[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

Be warned: encoding a DVD resolution video to h.264 in handbrake is very slow - it can take 2 or 3 times longer than watching the actual video even with a good processor. Encoding a HD video will be excruciatingly slow, I should imagine. The PS3 is happy with DVD resolution videos produced by Handbrake, but I've never tried a HD video. Good luck with that.

A couple of other thoughts:

Do you have a network attached storage device? You could transfer your videos over the network to the PS3 with that. It would be slow but you don't run into the 4GB filesize barrier. My PS3 sees my WD Mybookworld and can copy files quite happily.

Be careful with avidemux. Nice design - shame about the implementation. It has a tendency to lose audio/video synchronisation if you try cutting up mpegs. The video encoders it supports don't compress videos as effectively as H264, and last time I looked H264 support in avidenux was incomplete and unreliable. That might have changed though.

This last suggestion is a bit of a cop-out because it doesn't involve Linux. If you have a Mac or Windows, have a look at MPEG Streamclip:

[http://www.squared5.com/](http://www.squared5.com/)

That does chop up mpegs nicely without losing sync. The Windows version is an earlier one than the Mac one - the Mac one is better. You can get the Windows one working in wine but it's very clunky and slow in wine when you try to edit anything.

**EDIT**: if you do want to try out MPEG Streamclip, just use it for cutting up mpegs. My advice: don't use it for re-encoding. Been there, done that, got the scars. :(

---

### Post by morean51 on 2011-03-14
thank you for the sharing the website link which i really needed

---

### Post by xinate_dogix on 2011-03-14
coffeecat- thank you for your reply. unfortunately i do not have any network storage, i am planning on setting up a media server once i have enough money to build it :D. so i want to make this external hd work for now, plus i kinda like the idea of being able to take my media with me and hook it up to say a friends ps3. ill definately try handbrake, at least now i know that mp4 is a good direction to go. thank you again for your help.

---

