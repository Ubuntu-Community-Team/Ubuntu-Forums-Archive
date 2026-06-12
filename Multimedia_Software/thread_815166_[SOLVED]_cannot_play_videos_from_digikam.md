---
title: "[SOLVED] cannot play videos from digikam"
date: 2008-06-01
forum: Multimedia Software
---

### Post by quickk on 2008-06-01
Hi everyone, 

   I've installed digikam 0.9.4 beta 5 in order to manage my collection of pictures. I'm running ubuntu 8.04.  So far I like it, except for the fact that I cannot view any videos.  When I click on them it says: "No media player available".  If I right click and select "open with movie player" (or vlc, MPlayer, etc) the video plays fine.  

Here's what I tried: 

-Installing and running "kcontrol" to specify what to do with *.avi files (KDE components -> File Associations).  I have "Movie Player" then "VLC media player" then MPlayer.  Playing around with the order does nothing.

-Installing Kaffeine.  This works, except that the sound with Kaffeine is incredibly screechy and the video skips.  Using Kaffeine is therefore not an option.

-Starting digikam from the command line.  I get these messages when I click any videos in Digikam:
```

digikam: Search a KPart to preview MVI_0013.avi (video/avi) 
Cannot load metadata using Exiv2  (/home/amorris/Pictures/2004/Miscellaneous/MVI_0013.avi: The file contains data of an unknown image type)
digikam: Search a KPart to preview MVI_0013.avi (video/avi) 

```

From the looks of this, I need to specify the KPart to open the video.  What's a KPart?  Any help would be greatly appreciated.  Thanks!

P.S. Just remembered: for some reason, opening the videos did briefly function.  I just don't remember what happened to make it stop working!

---

### Post by quickk on 2008-06-01
Ok, this is completely messed up.  When kaffeine was installed, the video files would play from digikam (albeit the sound was horrible).  Now digikam won't play the videos even if kaffeine is installed.  The only thing that I can think of is that I ADDED kaffeine to the applications to open avi files with in kcontrol.  

Can anyone help, please?

---

### Post by Jamesmyname on 2008-06-04
I had the same problem and I've almost figured it out. A few things I did: 

- In kcontrol, "*.avi" wasn't listed in filename patterns in the avi section. I added it. 
- I added Kaffeine-Xine (xine_part) to 'services preferences order' under the 'general' tab on the top-right. 

Now in Digikam, I don't get a thumbnail preview of the video (not sure if this is supposed to be like this) but the video does play when I click on it. I'm less than happy with it though. There are no on-screen controls. I have to right-click for the menu with play controls. Also, I can't single left click to get back to the thumbnail views like I can with normal pictures. I have to click a new album then click back into that album I was in. Not very intuitive. 

Hope that helps. Good luck to us.

---

### Post by Jamesmyname on 2008-06-04
Sorry, double post.

---

### Post by Jamesmyname on 2008-06-04
Alright, I got it. Try using it with kmplayer. Go to synaptic and get kmplayer, kmplayer-base, and most importantly, kmplayer-konq-plugins (this is what threw me off the first time). 

Then in kcontrol, select .avi and move kmplayer to the top in 'general', then under 'embedding' add embedded mplayer for kde (kmplayer_part). Do it again for x-msvideo since it also handles .avi for some reason. 

Now in digikam, playing avi's works fine. I even have on-screen controls. However, no thumbnail, which is about half the usefulness of using digikam in the first place. 

Keep fiddling around with it and you'll get it. 

Any ideas on thumbnails? I'm pretty sure that it's a setting in kcontrol also. 

Good luck.

Edit: Got the thumbs to work by installing kdemultimedia in synaptic, plugins for avi as well. Now I can see .avi thumbs where I couldn't before in normal file browsing, Konquorer, and Digikam.

---

### Post by quickk on 2008-06-09
Thanks for the great info.  I had kmplayer and kmplayer-base installed, but not the kmplayer-konq-plugins.  I followed your instructions and now I can view the video files within digikam.  

There still are a few problems: 
-The controls disappear when playing the video file (I have to wait 'till the end to get back them back)
-I can't get back to the album thumbnail preview by clicking again on the video like I can with pictures.  Does this work for you?

After playing around I did figure out why I had managed previously to get totem or vlc to work with digikam.  After specifying my preferred video player in kcontrol, I went in digikam to Settings -> Configure digikam -> Albums, interface options.  If I select "Start Image Editor" instead of "Show embedded preview", then upon clicking a video file, the video opens up in totem (or whatever) in a separate window.  Unfortunately, this is not ideal for browsing regular images...

I hope that I can get these little problems fixed because I really like digikam!  Thanks again for taking the time to share your solution!

---

### Post by quickk on 2008-06-09
I forgot to mention one thing about the thumbnails.  To get them generated for video files, just make sure that you have the libarts1-xine package installed (I don't think that it is by default).  Once I installed this package, video thumbnails worked fine!

See this link: [http://www.digikam.org/?q=node/143]("http://www.digikam.org/?q=node/143")

---

### Post by quickk on 2008-06-09
To get back to the thumbnail view, press "ESC" (the escape key).

So apart from my disappearing controls while the video is being viewed, I guess that this problem is solved!  Hopefully other video players will work with digikam in the future...

---

### Post by planejason on 2008-07-04
sudo aptitude install kubuntu-desktop

installs all the KDE dependencies in one shot except it messes up your Ubuntu boot screen.  That can be fixed as detailed in post #5 of this thread:  [http://ubuntuforums.org/showthread.php?t=113202](http://ubuntuforums.org/showthread.php?t=113202).

I also use Amarok and other KDE apps and was tired of trying to find all the missing dependencies like K3B to burn cd's in Amarok so I just install the whole thing now.  It only takes up another 200 or so meg of disk space so I don't really mind.  You will still have to install libarts1-xine to get your video thumbnails however.  Happily playing my .mov files in digikam :guitar:.  Thanks for the great info.

---

### Post by planejason on 2008-07-04
ok sloppy coding in the post I linked to caused the sudo dpkg command to fail.  It should read:

sudo dpkg-reconfigure linux-image-$(uname -r)

sorry about posting before I actually tried it.

---

### Post by gedakc on 2010-12-16
I had a similar problem on Ubuntu 10.04 LTS Lucid Lynx Netbook edition.

Because f-spot does not import or handle avi video files, I had installed digikam with the following command:

     ```
sudo aptitude install digikam
```

This installed a lot of other packages related to KDE.

When I started digikam it would generate thumbnails for all of my jpg pictures but there was none for my avi video files.  To fix this problem I installed mplayerthumbs with the following command:

     ```
sudo aptitude install mplayerthumbs
```

This fixed the thumbnail problem with thumbnails not displaying.


At this point I could view pictures with digikam, but when I tried to play avi video files I could hear sound, but there was no video so I installed some missing xine packages with the following command:

     ```
sudo aptitude install phonon-backend-xine libxine1-plugins libxine1-ffmpeg
```

This fixed the problem.  :-)

Now I can see the avi file thumbnails, and when I click on the avi files in digikam, the avi files play showing both video and sound.


PS:  You can also substitute "apt-get" for "aptitude" in the above commands if you do not have aptitude installed.

---

