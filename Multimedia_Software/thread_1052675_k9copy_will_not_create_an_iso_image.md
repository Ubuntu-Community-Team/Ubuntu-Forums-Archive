---
title: "k9copy will not create an iso image"
date: 2009-01-28
forum: Multimedia Software
---

### Post by joriad on 2009-01-28
I have been trying to copy a dvd with k9copy but k9copy outputs the video and audio folders to a dvd folder and not as an iso image. this is how I have k9copy setup 

Input device: DVDRW SOHW-1693S  (/dev/scd0)
output device: iso image @ default
 
I then open the dvd and select the titlesets desired 
I then click the copy tab

After that a save image to disk window pops up and i select where I want to save the file to (usually to my desktop) 
location: i enter something like "family vacation" 
filter: *.iso

automatically select filename extension (.iso) is checked
finally I click save

under configure k9copy tab 
Devices tab: devices not detected by k9copy
dvd tab: output directory: /home/john/Desktop
         dvd size: 4700mb
         burn with k3b: checked
         autoburn: checked
         quickscan: checked
         use dvdauthor for copy without menus" checked
         one file/chapter (MPEG extraction) unchecked
         clear output directory on exit: unchecked

Everything starts out like normal. The backup progression window comes up and i see the preview. However, now I have a bunch of files poping up at random locations on my desktop for a couple seconds then disappear and new ones pop up and disappear throughout the copy process. They are named something like k9b******.tmp, also the output file created is a folder named "dvd" which contains the audio_ts and video_ts folders (not an iso file with the name that i selected) also k3b does not auto start after k9copy has finished. I also receive no error messages. I have used k9copy and k3b together before and had no problems like this, but I am unsure whether or not it was before upgrading to intrepid ibex. Does anyone know how I can get this working properly again?

Thanks
John

---

### Post by dskyracer on 2009-03-20
I am experiencing the same problem and am not sure if it is linked to the upgrade I did to Intrepid. Before I had no problem making ISO images with k9copy. I hope someone can give some help on this because I'm having to use a laptop now running XP and dvdshrink to produce the ISO images I need. For me K9copy does everything it used to do but then when it comes to the end point where a window appears saying it's burning and I believe this is the point where an ISO file is created.. the window just appears for a moment or two then disappears saying burn was done.. but no ISO is created but there are VOB files found in the video folder..Before, the burning window appeared for quite some time.. now it just disappears in seconds..  I liked using K9copy to back up DVDs and hope someone can come up with some suggestions on how to solve this. Thanks ahead of time..

---

### Post by mastermindg on 2009-03-20
Taken from Launchpad:

> Why does k9copy fail to make iso image after rippig a dvd?

K9copy rips the dvd no problem, but fails to make iso image at end of ripping and gives a message "DVD Burning finished"
 Kev said on 2008-12-01:

Hi RamonP
I too have lodged a question about this and had no answers... wonder if anything is being done about it [https://answers.launchpad.net/ubuntu/+source/k9copy/+question/52147](https://answers.launchpad.net/ubuntu/+source/k9copy/+question/52147)
I cannot seem to find any answers or work around on the forums as well.
 RamonP said on 2008-12-02:

Hi Kev!

The answer is simple. When typing the title for the iso image, do not leave
spaces between the words or just type underscores. It worked for me.

---

### Post by dskyracer on 2009-03-21
> **mastermindg said:**
> Taken from Launchpad:
     after reading this I tried backing up another DVD but didn't change any settings or try to name anything after clicking on copy. I just let k9copy go through the dvd and encode it. It's default settings seem to want to place the iso image in one's home folder. I let it do that. It went through it's paces and in the end when it showed the burn window it completed the task as it had in the past without quiting early. 
     Sure enough I found the ISO image in my home folder where I easily renamed it to it's proper title and then moved it to my ISO backups folder. So this may be the answer I was looking for. Just let the program put the iso where it wants by default then fetch it later and do what you want with it from there. At least that should work until the wicked developers come up with another fix. Try that and see if it works for you. 
     This doesn't mean no spaces in the title isn't the answer either. I just haven't tried that yet. I'm just glad to get k9copy to make an ISO image again. You can even watch the image or movie in Intrepid without using any special software to mount the image. Just right click on it and choose a movie program to watch the movie. I use VLC media player with great results. It's found in the repos. 
     With Windows one had to install a program like daemon tools to mount an ISO image in a virtual drive then choose a program to watch the video. I am loving Ubuntu Linux, It's powerful and very stable and secure. Plus the on-line community help is great too!  Thanks to all.

---

