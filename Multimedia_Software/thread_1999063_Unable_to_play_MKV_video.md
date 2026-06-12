---
title: "Unable to play MKV video"
date: 2012-06-07
forum: Multimedia Software
---

### Post by hiranyaroma on 2012-06-07
Hi, 
I am using Lubuntu 12.04. I am not able to play mkv files in my VLC player. The audio works fine but the video doesnt show. Please help.

---

### Post by andrew.46 on 2012-06-07
Can you post one of the problem files online somewhere?

---

### Post by hiranyaroma on 2012-06-08
It's a movie file. And its definitely not the file that has the problem, because I cant play any file in mkv format. I have tried quite a few with the same result. Only audio, no video.

---

### Post by willbe1kenobi on 2012-06-08
> **hiranyaroma said:**
> It's a movie file. And its definitely not the file that has the problem, because I cant play any file in mkv format. I have tried quite a few with the same result. Only audio, no video.

What video player are you using to play the file? If you can try a different player like VLC as this will come with the most common codecs for video and audio playback out of the box.

EDIT - I didn't read your first post properly. You may need to install the packages 'lubuntu-restricted-addons' and 'lubuntu-restricted-extras' (in a terminal just type in 'sudo apt-get install lubuntu-restricted-addons lubuntu-restricted-extras' then press enter, then enter your password then enter again and keep on pressing 'y' when you are prompted).

---

### Post by hiranyaroma on 2012-06-08
> **willbe1kenobi said:**
> What video player are you using to play the file? If you can try a different player like VLC as this will come with the most common codecs for video and audio playback out of the box.

EDIT - I didn't read your first post properly. You may need to install the packages 'lubuntu-restricted-addons' and 'lubuntu-restricted-extras' (in a terminal just type in 'sudo apt-get install lubuntu-restricted-addons lubuntu-restricted-extras' then press enter, then enter your password then enter again and keep on pressing 'y' when you are prompted).
Lubuntu restricted extras and addons are already the newest version. I have installed both the packages. Will this help? 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
I tried downloading medibuntu repo, but the terminal showed an error saying that a self signed certificate has been encountered.

---

### Post by SeijiSensei on 2012-06-08
Have you tried any other players?  I've found smplayer with mplayer as the backend will play just about any Matroska file I've thrown at it.

---

### Post by MartyBuntu on 2012-06-08
What are your computer specs?

---

### Post by hiranyaroma on 2012-06-08
> **SeijiSensei said:**
> Have you tried any other players?  I've found smplayer with mplayer as the backend will play just about any Matroska file I've thrown at it.
I have tried the default player in lubuntu (GNOME MPlayer) with no luck. After you suggested, I also tried smplayer. Unlike VLC this doesnt even play the audio.

---

### Post by hiranyaroma on 2012-06-08
> **MartyBuntu said:**
> What are your computer specs?
Computer Specs:

Memory: 2 GB
Processor: Dual Core AMD Opteron(tm) Processor 180 × 2 
Graphics: VESA: MACH64GM
Video card: Advanced Micro Devices [AMD] nee ATI Rage XL
OS type: 32 bit
Disk: 250 GB

---

### Post by willbe1kenobi on 2012-06-08
Is there any error message that is given to you by the program like saying certain codecs/libraries missing?

---

### Post by hiranyaroma on 2012-06-08
> **willbe1kenobi said:**
> Is there any error message that is given to you by the program like saying certain codecs/libraries missing?
Nope. None.

---

### Post by willbe1kenobi on 2012-06-08
Look in the preferences in VLC (press ctrl + P), click on the video button and on the output drop-menu and select a different option then save then play again (just also to make sure the check-box next to 'enable video' is checked).

---

### Post by hiranyaroma on 2012-06-08
> **willbe1kenobi said:**
> Look in the preferences in VLC (press ctrl + P), click on the video button and on the output drop-menu and select a different option then save then play again (just also to make sure the check-box next to 'enable video' is checked).
Yes. It is checked.

---

### Post by willbe1kenobi on 2012-06-08
> **hiranyaroma said:**
> Yes. It is checked.

and what about the 'output' have you changed it to something else. If not try that and check with all the options until you get to something that works.

---

### Post by hiranyaroma on 2012-06-08
> **willbe1kenobi said:**
> and what about the 'output' have you changed it to something else. If not try that and check with all the options until you get to something that works.
Oh, I had skipped that. A couple of options in the drop down menu of output work for me. Thanks!

---

