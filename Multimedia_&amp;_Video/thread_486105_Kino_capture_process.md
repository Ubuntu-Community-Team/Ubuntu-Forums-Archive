---
title: "Kino capture process"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by godtvisken on 2007-06-27
I am hoping someone can guide me where to start with this. I really don't want to do something that could damage my camera, so I wanted to ask first. 

What I want to do is capture video in Kino from my MiniDV camera over firewire. 

Most threads I have yet seen about Kino and 1394 seem to be about problems getting them to work. I guess I am not there yet. 

What I want to know, are things like.. 
[LIST=1]
[*]Must I plug the camera in before I boot up?
[*]Must I also turn the camera on before I boot up?
[*]I have heard that raw1394 is recommended over dv1394. When after I did "apt-get install kino", I found that this Kino version (0.9.2) and the way it is compiled (for ubuntu?) uses dv1394. In what ways is this disadvantages? Am I able to use raw1394 somehow?
[*] Do I simply go to the capture tab, press capture, and then play on my camera? (I suppose that is with dv1394? and that with raw1394 the controls would not be greyed out?
[*]Can Kino be used to put music to a video? (Yes, not related to the process, but something about which I am curisous ;))
[/LIST]

Thank you!

---

### Post by godtvisken on 2007-06-28
Bump ;)

---

### Post by godtvisken on 2007-06-29
:confused:

---

### Post by finite9 on 2007-06-29
> **godtvisken said:**
> 
What I want to know, are things like.. 
[LIST=1]
[*]Must I plug the camera in before I boot up?
[*]Must I also turn the camera on before I boot up?
[*]I have heard that raw1394 is recommended over dv1394. When after I did "apt-get install kino", I found that this Kino version (0.9.2) and the way it is compiled (for ubuntu?) uses dv1394. In what ways is this disadvantages? Am I able to use raw1394 somehow?
[*] Do I simply go to the capture tab, press capture, and then play on my camera? (I suppose that is with dv1394? and that with raw1394 the controls would not be greyed out?
[*]Can Kino be used to put music to a video? (Yes, not related to the process, but something about which I am curisous ;))
[/LIST]


1. no, not needed, just plug it in before starting kino, but should even work after starting kino
2. not needed, just turn on dvcam when needed i.e. before capturing
3. raw1394 is more secure...doesnt let ieee1394 devices have unneccessary access to linux box.  dv1394 is less secure, but if its only a single user pc then doesnt really matter that much.
4. start kino as sudo to be able to capture: Press ALT-F2 then type "gksudo kino".  This will allow you to use the dv1394 capture tools without having to modify udev permissions on your ystem.  There is a guide on kinodv.org for how to modify permissions for udev so that kino can be started as normal user and still capture.  Once started, just go to grab, and make sure that status bar at bottom of screen says that dv1394 started ok.  Then either use the dv controls to capture or just press play on the dvcam and hit the record button in kino.
5. In the FX tab, you can use the audio filter Dub to add an audio file, BUT, you must choose if you want to overwrite the existing track or create a new track.  I have never tried this, so I do not know if you can "create" a new track that will merge with the existing sound track, but overwrite mode should work fine for movies without sound where you just want to add a music track.

Hope that helps.

---

### Post by godtvisken on 2007-06-29
Yes, thanks so much

---

### Post by Brian96 on 2007-07-07
For me, I found that I did not need to start Kino in gksu (as root). Doing so enabled the AV/C controls, but it also created the capture files with root permissions. I don't know that this is a problem, but I am pretty wary about permissions stuff after some previous problems.

Anyway, Kino works pretty much out of the box for me. To capture, though, I have to click "Capture" on the interface and then "Play" on the DV camera (within 10 seconds--Kino counts down). Everything works fine from there.

I do have a question about Kino, though, if anyone can answer it. For comparison purposes I captured the same DV tape in Windows with Sonic and in Kino. When I exported it to mpeg2 in Kino the resulting "mpeg" file for 62 minutes was 2.3 GB but the "mpg" file Sonic created was 3.6 GB for the same content. Anyone know why this is?

---

### Post by finite9 on 2007-07-07
the only thing I can think of is that the quality setting used in the script that Kino uses to export to mpeg is different than the quality setting used by Sonic.  Usually, quality is determined by bitrate, and the higher the bitrate the larger the file size, but there is a point of diminishing returns, but maybe Sonic figures that they'll set the bitrate higher than really needed just to get max quality out of the video (at the expense of an extra Gig)

As I said about permissions in my earlier response, you can fix this by editing the udev permissions, then you dont need to start kino as root to capture.  I capture as root, then change file permissions by hand then edit as user, because I have not yet had time to investigate editing udev, but it really isnt a hassle for me so its low priority for me at the moment.

---

### Post by Brian96 on 2007-07-07
> **finite9 said:**
> the only thing I can think of is that the quality setting used in the script that Kino uses to export to mpeg is different than the quality setting used by Sonic.  Usually, quality is determined by bitrate, and the higher the bitrate the larger the file size, but there is a point of diminishing returns, but maybe Sonic figures that they'll set the bitrate higher than really needed just to get max quality out of the video (at the expense of an extra Gig)

As I said about permissions in my earlier response, you can fix this by editing the udev permissions, then you dont need to start kino as root to capture.  I capture as root, then change file permissions by hand then edit as user, because I have not yet had time to investigate editing udev, but it really isnt a hassle for me so its low priority for me at the moment.

Thanks for the info.

As for permissions, I found the only thing lost by running kino normall was the AV/C controls. So I just manually press play on the DV camera and don't have to worry about permissions on the created files.

---

