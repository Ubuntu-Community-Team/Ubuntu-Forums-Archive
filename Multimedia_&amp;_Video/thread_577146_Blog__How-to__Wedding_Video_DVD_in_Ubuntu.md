---
title: "Blog / How-to : Wedding Video DVD in Ubuntu"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by Statik on 2007-10-15
Hey all,

I've been using Ubuntu for a while now and I've really appreciated the How-To's I've found here. I've been working towards editing and producing a Wedding video DVD that I was supposed to have done 4 years ago, and I think I've finally found everything I need in order to do it all in Ubuntu.

So, in trying to give back to the community, I thought I'd blog the steps I'm going through to create the project, hopefully answering questions and revealing software and techniques along the way. My way of giving back to the community I guess.

So, step one: Capture video from DV camcorder. Software of choice? Kino

Why Kino? Well, three basic reasons:
1. Its in the repositories
2. It controls the camcorder directly, no button pushing
3. It detects scenes as well as has a file size limiter so that it won't kill my FAT32 partition.

FAT32 partition? Well, I have a bit of an odd setup. I have 3 HDs and 2 OSs, One EXT3 Linux drive that only Linux can see, One FAT32 drive that both OSs can see and One NTFS drive that isn't setup in Linux, effectively hiding it. 

Because of space issues, I'm capturing the DV to the FAT32 drive but doing my editing on the Linux drive.

OK, so, the how-to

First, use Synaptic to install both Kino and DVGrab.
Next, there is a permissions issue with the IEEE1394 module. For now I'm just band-aiding it with CHMOD each time I boot. The command is as follows:
```
sudo chmod 777 /dev/raw1394
```
Yes, this can present a security risk, but its sufficient for what I need right now.

I have 6 tapes of video from 2 cameras. They are labled 1a, 1b, 1c and 2a, 2b, 2c

So, first, boot up Kino. 
Go to Edit->Prefrences
Here are screen-shots of the tabs I used.
[IMG]http://www.statikonline.com/Slides/Kino_01.png[/IMG]
[IMG]http://www.statikonline.com/Slides/Kino_02.png[/IMG]

Once you're done, hit the CAPTURE tab on the right-hand side of the Kino window.
[IMG]http://www.statikonline.com/Slides/Kino_03.png[/IMG]
Pop your tape in, if its not rewound, hit the |<< button to rewind to the beginning of the tape. When its ready, just click the big red capture button and go for coffee. It takes 1 hour for 1 hour of DV to download.

I'm just finishing doing this for the six tapes tonight. More as I continue with the project. The goal is to use only Linux, produce a professional looking product, and have it to the couple for their 5th anniversary.

Statik

---

### Post by greenstar on 2007-10-17
Looks great so far. I'll be camped out, watching. I've done a fair bit of DV work myself, though it has been a while since I've had time. While I'm hanging out, I might be of some use, and I might learn something also. Great choice of HowTo topic. 

Greenstar

---

### Post by stinger30au on 2007-10-17
this ubuntu distro may come in handy

[http://ubuntustudio.org/](http://ubuntustudio.org/)

---

### Post by Statik on 2007-10-17
stinger30au:
I've seen that Distro, but I'm trying to stick to a vanilla install if I can since that's what I have. I haven't done any special tweaking that I recall. Hopefully everything will be workable for most users this way.

greenstar:
Please feel free to add comments, hints, or even your own instructions. I'm relatively new to this on the Ubuntu front, and not that experienced in any other OS either, but I'm learning and thought since there wasn't already a tutorial I'd try to add one.

Statik

---

### Post by Statik on 2007-10-20
OK, so now you have all of your video captured into your computer as DV files. Mine are captured according to the tape they were on so I have a structure that look like:
[IMG]http://www.statikonline.com/Slides/Wedding_2_1.png[/IMG]
And each directory looks similar to this one:
[IMG]http://www.statikonline.com/Slides/Wedding_2_2.png[/IMG]



So, what are you going to do next? Well, the next thing to do is to recreate the sections you planned before you even went to the wedding to shoot . . . you did plan, right? :) Anyway, what we are doing is figuring out the basic sections for individual sections of the DVD. There are basic topics that you can pretty much depend on in a wedding, so we will create directories for each. My structure looks like this:
[IMG]http://www.statikonline.com/Slides/Wedding_2_3.png[/IMG]



Then we fire up our video editor again. I'm still using Kino at this point because I'm having some trouble with the audio output quality of KDENLIVE. I'm hoping to have it resolved by the time I get to the next phase. I should also note that I tried KDENLIVE's capture funtionality. It didn't work. The latest version of KDENLIVE requires DVGRAB >= 2.0 in order to capture video. Ubuntu comes with 1.8 I tried upgrading to the latest DVGrab, from the website, 3.0, but no joy. Thats another project for another day. For now, fire up Kino and open the first clip.
[IMG]http://www.statikonline.com/Slides/Wedding_2_4.png[/IMG]


Here what we are going to do is select the EDIT tab on the right and then hit PLAY. When we get to the start (or end) of a section we want, we hit stop. Then we use the |> and <| keys to move forward or backwards one frame at a time until we get what we want. Then we hit the <-|-> key at the top (split scene). This cuts the clip into two clips at our current cursor position. If we didn't want the first section, we can click on it and then hit the scissors to CUT the scene. Continue on this way until all you have left is the scenes you want. Make sure you leave yourself about 2 seconds at the start and end of a clip if you can. They make good places for fade in and fade out.
Once all you have is the short clips you want, click on the export tab. In that section, we are going to use the DV File section. Here is my setup. You can change the prefix and the output directory. I'd recommend sending them to the Sort parent directory so you can rename and sort them from there.
[IMG]http://www.statikonline.com/Slides/Wedding_2_5.png[/IMG]



Continue along and do this for all of your captured files. Eventually you should have all of your SORT directories filled with some clips you'd like to see in those sections. If you want a clip in more than one section, just use the gnome copy/paste in nautilus.

Thats it for now. I have 6 hours of video to chop and sort!

Good luck!

Statik

---

### Post by Statik on 2007-12-30
Just in case you are wondering what's happening with this blog . . . I'm still cutting up the video. Between 4 kids, sailing with the Navy, my wife being pregnant, and other problems, its been difficult to get time to chop the 6 hours of video up. Especially when you're concerned with frame-accurate cuts. I'm almost done 1 of the 6 tapes. However, the other tapes should have longer cuts (the ceremony) or longer sections to delete (greeting camera during reception).

Before I edit the footage together, I think I'll do some color correction on them so I'll go over that next . . . once I'm done the cutting of course.

Statik

---

