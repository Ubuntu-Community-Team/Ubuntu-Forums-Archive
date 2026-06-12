---
title: "messed up realplayer audio second try"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by 900donuts on 2007-03-08
I made a post acouple weeks back complaining of slow, distorted, and alaround messed up sound and no suprise no one answered me

so i took a second look 

i right clicked on a not working file and checked the video tab in the properties window (note it didn't say video&audio) 
they all said real video 4.0 and the and didn't say a thing about audio

i then checked a working file all working files gave me info on the files audio and video

H:mad: W D:mad:  I FIX THIS!!!!!

---

### Post by Metaljaz on 2007-03-08
Is your problem with realplayer or it is with your soundcard? If its a realplayer problem try reinstalling. 

Assuming that you downloaded RealPlayer10 from [www.real.com/linux](www.real.com/linux)

To install realplayer place the file in your home folder
make the file executable: From the terminal window type:

chmod a+x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
enter password
To complete the path where you want to install realplayer type:

/opt/RealPlayer

to begin copying files accept the default
allow the installer to configure systemwide symbolic links
when asked to specify the prefix for symbolic links just press enter

---

### Post by 900donuts on 2007-03-08
the problem defiently is not the sound card
my computer does not reconize the existance of audio in these files
i pluged one of the non working files into a windows and right clicked it to bring up the properties it only said real audio/ real video 4.0
its clear that the linux computer dosen't have the files to reconize the audio part 

how do i add suport?

as for reinstall im not willing to go that far yet

---

### Post by Metaljaz on 2007-03-08
Maybe i am a little confused. Are you using firefox and trying to play streaming audio/video files or do you just have a file that you are trying to use realplayer to open and play?

---

### Post by 900donuts on 2007-03-08
i have a collection of video files (favorites from brickfilms.com)
the audio on some does not work when i play it it sounds like its in slow motion(the video is playing normal and the audio is trying to keep up distorting te sound even more)

---

### Post by Metaljaz on 2007-03-08
If you are using firefox type the below command in the address bar and look 
for your realplayer plugin:

about:plugins


Mine works fine for all audio and i have the following results under Realplayer


Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.2.0 on Jul 18 2006

---

### Post by 900donuts on 2007-03-09
i'm not using firefox
the files are downloaded and stored on the hard drive

heres what you should do 
1. go to [www.brickfilms.com](www.brickfilms.com)
2. download the film named woot! (don't worry its g rated)
3. come back and tell me that it plays just fine

---

