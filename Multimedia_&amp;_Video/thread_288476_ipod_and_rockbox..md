---
title: "ipod and rockbox."
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by BlaineM on 2006-10-29
I installed rockbox onto my ipod for use of the .ogg songs in my library on my Ubuntu machine.  But when I plug the ipod onto the machine and try and write music to the ipod, it does not let me do it.  Sometimes even the ipod does not mount and allow me to view the files on it.  Why is that... and how do I get to add the songs to it from simply dropping them in.  The only way so far that I get to write to the ipod, is in windows... but that would mean that I have to get my library of .ogg (which isnt very big, but would take a long time) to my laptop windows side, and write them in that way.  Im thinking that it may have to do with the format of the ipod, although I think that it is written for windows which would be fat32... so Linux should not have a problem with reading, and writting to it.  Is it a permission that I do not have set to be able to write to the disk of the ipod?

Can someone explain to me what might be going on, or try and lead me in the right direction as to how to figure out what is going on with this situation.  I would really like to learn about how this can be fixed, or just learn about it.

Thank you,

---

### Post by BlaineM on 2006-10-30
nevermind... I found the answer.  It was formatted in FAT32, which was the problem.  It needed to be the ext3 which I just needed to format using another installer so Linux could write to it.  Google and Forums are my friend, and a great resource.  I am now using ipod linux which is uClinux, and podzilla which is the "desktop" for it.  It runs great.

---

### Post by BlaineM on 2006-11-04
also got Rockbox installed.  I like the interface options, and the level meter that is has.  I like mostly that I can play .ogg files on it, instead of reripping the collection.  It does not have any problem with playing as it is supposed to.  But then again they are not high bitrate, which I heard are supposed to give problems.

---

### Post by BlaineM on 2006-11-04
I am now posting two more replies to get the bean count to 60.  here is the first.

---

### Post by BlaineM on 2006-11-04
and here is the second.  yeah, I have reached the mark.

---

### Post by Drezliok on 2006-11-04
Rockbox?

How well does it work?

---

### Post by BlaineM on 2006-11-16
it works very well.  I cant seem to get the sleep to work, so I have to do a reset... middle button and the menu button at the same time, and then in the ipl loader screen select the sleep option.  my battery on this ipod is almost shot.  it doesn't last very long even running the appleOS, so I cant tell you about the battery consumption amounts for Rockbox.  It seems to work well, and not drain too fast.  

I have had a problem though with regard to running the level meter and playing songs.  If I have the scope of the level meter too high, sometimes it will lock up, and I have to reset the ipod, load rockbox, and replay the somg that I am running.

I would say that it is good to play with things like other OS on the Ipod, but sometimes just creates more work, which to me is fun.  But sometimes I want things that just work.

Blaine

---

### Post by trstn on 2006-12-02
Did you have any problems getting your ipod to mount in ubuntu with rockbox? Windows i´m fine but nothing happens but a shrill double beep when i plug it into my ubuntu box.

---

### Post by BlaineM on 2006-12-06
no, I have the full options to write to the disk directly... that is how I put the songs on the ipod... drag and drop.  I since have changed the setup though, I now have ipod linux, and rockbox under the iploader, which gives the boot options.  But I write into the part that holds the rockbox folders that I can then read and play with rockbox.  I dont even boot into ipodlinux, only to show people what it functions like when they ask.

---

