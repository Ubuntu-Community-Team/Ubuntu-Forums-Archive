---
title: "Capturing Video from an old CCD-Sony TRV65 NTSC"
date: 2009-05-19
forum: Multimedia Software
---

### Post by jaime256 on 2009-05-19
I have been trying to capture video from an old sony HI8 video camera to my computer. First of all, this is an old camera without usb or firewire ports. It only has S-VIDEO and RCA jacks. Nothing else. Some people suggest using a new dv cam, unfortunately I already have this one so I can't go out an buy another as many people may suggest. Finding a way to use this old camera would be nice since mine still works.

I bought the Diamond VC600 usb video capture to see if I could do this, but unfortunately it doesn' work. [http://www.diamondmm.com/VC600.php](http://www.diamondmm.com/VC600.php)
I can't find any help other than their live help on this page. So I couldn't get any other information on it. I don't have a windows machine so I haven't tested it on that just Ubuntu.

I also tried to capture from the Qsee usb dvr which is used for security cameras. I always thought I could use my video camera like a webcam, but didn't try it until today. This Qaee worked on windows, but not on linux. [http://www.q-see.com/products/security-product.php?ProductId=134](http://www.q-see.com/products/security-product.php?ProductId=134).

Unfortunately none of these two are working for me under Ubuntu 9.04 64-bit. They both have windows programs. I can see both under lsusb but can't capture anything from either one. I have tried kino, but that only uses firewire which is useless even if I had a port. I know there are other tweaks since I went through all the 10 pages of postings for video capture and still nothing I can use. Some of the programs I have used are kdenlive, Pitivi, VLC, xawTV which doesn't even open. I have also tried using camorama and cheese to capture video, but I got nothing on /video/device0.

I'm attaching the lsusb output. The cypress is the information for the Qsee and the Diamond actually says diamond on it. Any help on a card that may work or other information is appreciated. If not at least list the card(s) you have tried so we know which one if any you have tried. Here's a listing I also found that may help a bit. I may try an internal card that I saw at the store and see if I have any luck with that one when I return this one. My board on has one pcie port too so that makes it a bit harder to find anything I can put in there, hence the reason for the usb capture card.

 I wanted to try a tv card with svideo, but I wasn't sure if any of them worked with Ubuntu (linux) either, at least for the few cards that were available. Here's a nice site with what seems to be some good basic information. [http://hardware4linux.info/type/87/](http://hardware4linux.info/type/87/). So far I still have no luck with either of these two pieces of hardware.

---

### Post by jaime256 on 2009-05-19
Okay, I just did a clean install of Windows XP on another machine and tried to download the Diamond driver for their VC600 video capture. Guess what, there's a folder there but it's empty. I downloaded that on both the windows machine and the ubuntu machine and I get the same thing. I just want to see if this thing even works and I can't find any cd for the drivers so I can't remember if this thing even came with one. Although the manual tells you that's what you need to do, use the cd in order to install it. So I emailed their tech support and this is the screenshot of what you get after sending out that online email to their tech support. This thing may be going back sooner than later since I can't get it installed anywhere.

---

### Post by lisati on 2009-05-19
I have an old Hi-8 camera as well. I haven't had much joy importing using a video capture card with it either (variable results), and on the rare occasions I use it these days I tend to use a DVD recorder to transfer to a DVD-RW and then import the DVD contents to my PC.

---

### Post by jaime256 on 2009-05-20
I hear you. I'm online with a person at diamond right now...waiting for the drivers since they are not in that zip folder. It's empty so we'll see. I also have that windows machine ready to try it, but since the cd is nowhere I don't think I got one. I'll keep posting here if I do find anything. I don't need to buy a new camcorder yet. I don't have anything other than the camera and computers without any imputs for this. So I had to try something. Here's my chat with the guy. I didn't get a chance to read his linux response so I asked about it at the bottom before he cut the conversation off. But at least there's your answer on the Diamond hardware regarding Linux.

UPDATE: Well, I'm a knuckle head. I found that cd in the box that was under the desk. Anyway I got the program installed in windows and it seems to work. You can make mpegs and avi files which is good. The quality is okay, but then again it's an old camera so I didn't expect anything special there. So there you have it. I just had to resort to windows to make this one work.

---

### Post by jaime256 on 2009-05-22
Now that I got the video, I had about 38 gigs for about 35 minutes of video. Unfortunately the sound didn't get picked up. I did plug in the cables, but maybe I it had to do with the sound on the computer. I can remember if the sound drivers were installed since I never checked it. In this case it's not so bad because I can just add music.

Since I extracted the file as an avi, I have no idea what would be the best file but I know avi's can be streamed nicely that's why I used that. I ended up importing the file to kino which allowed me to so that was good. Kino uses it's own file to make this happen which is fast since you don't have to wait for the whole video to get imported and works at the normal video speed. This part is pretty good and fast. I was then able to cut the parts I didn't want. I like the simplicity of kino for this. Unfortunately you have to install mjpegtools I think it was in order to export the file to something else. If yours doesn't work, look on the bottom of your kino window, the error will show there letting you know what you need which was great. This is where my other problem was, couldn't export to anything even after I installed the tools (you have to restart the proggie in order for them to work) until I tried ogg best. Then something started working. This took about an hour, so if this part works you can just take a break. I just went to bed since it was way too early in the morning. I spent all day just on one video and now on my second day.

Now, can someone tell me what's the best way to add music to an ogg video file. Oh yeah, the ogg file is now about 4.7 gigs so that's a huge improvement. If I can add music and youtube it, then at least I got one way of making a video. I also have kdenlive installed if this helps? Just need help  on how here...anything anyone?

---

### Post by jaime256 on 2009-05-23
Good news. I kind of figured out how to add music to my video since I really didn't care about all the noise the camera picked up anyway. Here's what I used. Kino for the editing, cutting and mating the parts I wanted. Kino allowed me to make an avi but nothing else. So on to the next program.

I decided to play with kdenlive since I already have it installed. You can also just drag and drop your .ogg or .avi file into the window on the left called the project tree. I also chose some mp3 files and dragged and drop them here as well. No conversion needed from what I could tell. This took me a while to figure out since I have never done video and don't really care to just because they take forever to do. On the bottom time line, just drop your video on the first line, then the audo files on the second. If you look at the tiny controls at the very bottom of your screen, I suggest you use those because they help a bit. This is pretty much the basics of this program, you have to play with it to figure out what each thing does, but it's what took me forever to figure out so there you go.

The odd thing with this program is that I can drop the .ogg or or avi file, but I was only able to make and avi file, the ogg kept crashing on me. So it's the opposite of kino for me. The version on the ubuntu repository is 4.2.2 for Kdenline. It's what I have. My kino is 1.3.0. The other problem I found was that when I played the video along with the audio it was very choppy for me. So you can't tell where your audio ends that way, but since I just put them one after the other, which is very easy, just drag and drop next to each other and that's it. The music gets chopped of this way though even if your song is good, so I just added some audio fade in and out to get rid of that. Yeah there's a pause of silence until the next song begins, but it's fine otherwise. Now if I can only stop the damn thing from crashing it would be nice. It crashed on my avi so it didn't finished the video. I wasn't even using the comuter. It takes long so that makes it very unusable if you ask me. If the program can't stay on it's just not worth waiting for an hour or two just to find out it crashed. This was my experience, but I hope this helps.

I wish kino did the same thing. I did read somewhere that it does support different type of files, but I tried dragging my mp3s on there and that just didn't work. I just like kino because the video parts were just smoother. None of that choppy stuff.

---

