---
title: "I cant import video from my Kodak Playsport"
date: 2011-05-15
forum: Multimedia Software
---

### Post by CharleyGnarlyP290 on 2011-05-15
I have a Kodak Playsport video camera that has worked quit well for what I do. In Windows I was able to plug it in, the Kodak Media Impressions software would open, and I could import the video and them perform simple video editing. I could also burn it to DVD once I was finished, load it to youtube, save it to my harddrive. 
When I plug it in on Ubuntu, it opens up and says that I have photos available (instead of video) and when I try and play the video it plays about three frames in a 15 sec clip. Basically, like snapshots.
Is there a program I can load to accomplish what I was able to do on the kodak software?
I have been using Ubuntu for about a week so please talk real simple. :)

---

### Post by USAFSS on 2011-05-22
> **CharleyGnarlyP290 said:**
> I have a Kodak Playsport video camera that has worked quit well for what I do. In Windows I was able to plug it in, the Kodak Media Impressions software would open, and I could import the video and them perform simple video editing. I could also burn it to DVD once I was finished, load it to youtube, save it to my harddrive. 
When I plug it in on Ubuntu, it opens up and says that I have photos available (instead of video) and when I try and play the video it plays about three frames in a 15 sec clip. Basically, like snapshots.
Is there a program I can load to accomplish what I was able to do on the kodak software?
I have been using Ubuntu for about a week so please talk real simple. :)

I just purchased a Kodak Sport - I also have a Sony Bloogie Touch - They should both work the same way.  Connect them to the USB port, then turn it on (this will start the mass storage mode), then you should get a message to open the memory with sever options (Shotwell Photo Manger, Open Folder, Do Nothing, Open With Other Application), SELECT OPEN FOLDER... OK

DO NOT OPEN FILES FOR YOU VIDEO IN SHOTWELL PHOTO MANAGER.

On the Kodak Sport, you'll enter a folder called DCIM, it may say 100 SPORT, enter that folder, that should hold your .MOV files

You can drag and drop them to a folder on your desktop, or whatever... 

Next question, video editing programs.  You are correct that the software loaded on to Flips, Bloggie and Sport will not work on Linux, but you can download a number of programs free via Ubuntu Software Center: Kino, OpenShot, Kdenlive, Avidmux and others.

If you have not done so, upgrade to Natty 11.04 -- or back-up you files on an external hard drive and install 11.04 from scratch. 

You'll find that people in the Linux community are happy to help you succeed. :D

---

### Post by eric-yorba on 2011-05-25
> **USAFSS said:**
> DO NOT OPEN FILES FOR YOU VIDEO IN SHOTWELL PHOTO MANAGER.
Yikes! Why not?

---

### Post by R.A. on 2011-06-10
This might fit here:

I encounter some problems when working with the .mov files I extracted from the camera. I want to edit them but I am unable to do that. Opening in Avidemux gives me an error because of ¨B-frames¨. I´m not tech savy so this doesn´t say much to me. I try to transcode them with transcode but it gives an error saying it doesn´t recognise the codec.

I used tutorials I found on the internet, I can not get them to work.

Perhaps someone here can shed some light on this?

---

### Post by CharleyGnarly on 2011-06-16
So far I really like Ubuntu, but this is one area that is frustrating me. I recorded a really short video in the lowest quality possible on the Playsport, and plugged it in. I opened the DCIM folder and tried to play the video, but it was pretty choppy.
The laptop is five years old, but should be able to play lower quality video fine. I used to play DVDs on it all of the time when I had Windows loaded.
I want to be able to load and edit video, but can't seem to find a definitive answer.

---

### Post by eric-yorba on 2011-06-17
> **CharleyGnarly said:**
> So far I really like Ubuntu, but this is one area that is frustrating me. I recorded a really short video in the lowest quality possible on the Playsport, and plugged it in. I opened the DCIM folder and tried to play the video, but it was pretty choppy.
The laptop is five years old, but should be able to play lower quality video fine. I used to play DVDs on it all of the time when I had Windows loaded.
I want to be able to load and edit video, but can't seem to find a definitive answer.

Did you play the video from the card, or from your HD?  If it was the former, try copying the file to your HD first for better performance.

Second, what program did you use to play the video?  You can try Totem, VLC, Mplayer, etc. 

And lastly, do you have the manufacturer's video drivers installed for your video card?  That's often a huge pain on Ubuntu, but it can help make video performance significantly faster.

---

### Post by CharleyGnarly on 2011-06-17
Well, I have figured out the problem. My Laptop just can't handle video. It is too old and both the CPU and GPU are not up to the task. Not really a problem since it was my Ubuntu experiment to begin with. I can rip musice and surf the web and that is fine with this laptop.
I loaded some 720p and lower video to my desktop and was able to play and edit both with no problems. I will try 1080p next, but doubt I will have any problems since my desktop can play 1080p in Windows just fine.
Thanks for all of the help.

---

