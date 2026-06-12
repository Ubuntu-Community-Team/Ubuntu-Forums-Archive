---
title: "[SOLVED] No Artist Name on Sansa Files"
date: 2008-06-14
forum: Multimedia Software
---

### Post by shelbyvision on 2008-06-14
Hi,
In my quest to make myself windows-free, I have just turned my attention to my mp3 player, a Sansa Clip. I was able to easily navigate to my music folders on my external hard drive, and with the Sansa plugged into the computer, Ubuntu automatically recognized it. I simply copied and pasted music from my archives to new folders I created on the Sansa Clip. It worked fine, except that even though the Sansa has the songs individually labeled correctly with the name of the song and the artist, when I try to find them on the Sansa, under artists or albums, they are listed under "unknown". I suppose I need to use some application to make the Sansa to get it right, but I'm clueless. Any ideas out there?
Thank you,
Steve

---

### Post by shelbyvision on 2008-06-15
Hmmm, no replies. Maybe I wasn't clear about the problem. I'm uploading songs to my mp3 player (Sansa Clip) from my archives on an external hard drive. This works fine using copy/paste, but when I try to find those songs on the mp3 player, instead of being listed under the artist names, they are listed under "unknown". I got Exaile music player, and tried using that to upload to the mp3 player, but have had no success with that yet. How can I get the songs to be listed under the artist's names instead of "unknown"?
Steve

---

### Post by compacho on 2008-06-16
Hey Steve. Before I bought the Clip I knew going in that the device wouldn't read file names. Just tags. So before my device arrived in the mail, I did some reading around for good tag editors and came across EasyTag. It's in the Repos and it'll automatically tag all your songs just by reading the filename.

You can also use players like Banshee and Amarok to do it but its not as fast.

I wanna know something though, when you plug in your player, does it show up as an external drive or an mp3 player? And can you get Ubuntu to recognize it in MTP mode? I can only get the device to be read in MSC mode. Sadly, the device doesn't show up in Banshee and Exaile :(

---

### Post by shelbyvision on 2008-06-19
> **compacho said:**
> Hey Steve. Before I bought the Clip I knew going in that the device wouldn't read file names. Just tags. So before my device arrived in the mail, I did some reading around for good tag editors and came across EasyTag. It's in the Repos and it'll automatically tag all your songs just by reading the filename.

You can also use players like Banshee and Amarok to do it but its not as fast.

I wanna know something though, when you plug in your player, does it show up as an external drive or an mp3 player? And can you get Ubuntu to recognize it in MTP mode? I can only get the device to be read in MSC mode. Sadly, the device doesn't show up in Banshee and Exaile :(

Thanks for the reply. I had given up on anyone replying, so I hadn't checked back in quite a while.
I'll give EasyTag a try.
To answer your question, when I connect the Sansa Clip, it shows up as "disk" on the desktop. If I click on Properties, it calls it a "removable hard disk" with vfat file system. I can't find any mention of mode anywhere. Where do I find that?
Steve

---

### Post by shelbyvision on 2008-06-21
I did some searching for answers and found this at this url[http://www.micahcarrick.com/05-21-2008/sansa-view-ubuntu.html]("http://www.micahcarrick.com/05-21-2008/sansa-view-ubuntu.html")
It's about Sansa View, but it worked for my Sansa Clip.
I dragged and dropped the songs onto the Sansa Clip and it automatically created a folder with the artist's name!
Here are the instructions I used:

By default, the device is in MTP (Microsoft Transfer Protocol) mode. More on this later. Most of us linux users are used to using MP3 players in MSC mode which is essentially just a USB flash drive.
Mounting the Sansa View in MSC Mode:

To mount the device in MSC mode, you put the device in hold (slide the power switch down) and then hold down the left button on the direction pad for about 5 seconds and then connect it to your USB port. The device should then auto mount into '/media/Sansa View' as a flash drive and an icon should show up on your desktop.
Getting Rhythmbox To Identify the Sansa View in MSC Mode:

Rhythmbox will not initially identify the device. To get rhythmbox to see the device, you simply place a text file into the root directory of the player named '.is_audio_player' (/media/Sansa View/.is_audio_player). Then it will show up in Rhythmbox and you can drag and drop your music onto it. However, rhythmbox seems to copy the music into the root instead of the 'MUSIC' folder. To change that behaviour, you can edit that '.is_audio_player' file to tell it where to copy the music. The following should work good for a '.is_audio_player' file for the Sansa View:

audio_folders=MUSIC/
folder_depth=2

---

### Post by shelbyvision on 2008-06-22
I did some playing with the process and found the easiest way to do it.
First, open EasyTAG and open a folder of songs. The preferences need to be set to write ID3v2.3 tags, with ID3v1 unchecked. The whole batch of songs can be processed at once, using the Fill Tag scanner, with all the songs selected at once. Clicking the # button will give each track a number. Clicking save will update all the files in their folder. 
Second, open the mp3 player's Music folder, and create a new folder for the songs just processed. Then simply copy the songs from the file browser and paste them into the new folder. When I disconnect the mp3 player and go to Music/Artists, there's the new artist's name, with all the new songs.
Almost as easy as Windows. ;)
Steve

---

