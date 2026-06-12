---
title: "Choppy Surround Sound"
date: 2012-02-05
forum: Multimedia Software
---

### Post by microsuperman on 2012-02-05
I have a Asus A8N-SLI Premium and I am running 11.10 
  
 My built in sound is 

                                   
```
~$ lspci | grep audio 
 00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2) 

```My problem is when I have my sound output set to 5.1 all my speakers are choppy even the sub. Its like having someone muting and un-muting my sound constantly. I know it is not muting, for when I turn the sound way up I can hear it whisper what sounds muted at normal.

 When I have done a sound check I get "fron... eft" and the same with all the other checks. I have played it it a bit and and found that 4.0, 7.0, 7.1, and stereo all work without a problem. I would settle for 4.1 but it is just as choppy.  
 I have had this problem since started with 8.04, 32 and 64bit. I just have never wanted to deal. a.k.a. all my music is in stereo.  
 

  So if anyone could point me a the right direction that would be great.

---

### Post by microsuperman on 2012-02-09
Bump :sad:

---

### Post by Arcturus691 on 2012-02-27
I am also having the same problem on a different chipset: 

If I have my sound set to analog stereo input and test the speakers the left and right channel work and there is no choppiness in the sound, If I change my setup to 5.1 then I have problems, the sound cuts in and out, the test sounds do not come out on the correct speakers.   I am not sure if your board is like mine, I have three 3.5mm jacks in the back that you can configure for surround sound.  I was thinking that maybe this is related to the issue.  I tried configuring the jacks using the command alsamixer to no luck.  If it is not the same issue let me know and I will start a different thread.


-----------------------------------------------------------
!!Soundcards recognised by ALSA

 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC655 at irq 22

!!DMI Information

Manufacturer:      MSI
Product Name:      MS-7310
Product Version:   10
-----------------------------------------------------------
You can get the above information by running the command:

wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh

the command gets your system info and posts the report on a url at the alsa project site.  Try running the command and post the results

---

