---
title: "Easy Way to grab desktop sound with Sox"
date: 2011-07-16
forum: Multimedia Software
---

### Post by shantiq on 2011-07-16
sometimes one wants to just grab desktop sound 


and this here really works well


[B]
1.[/B] Install pavucontrol and sox  ( pavucontrol for sound monitoring and sox for recording)



   ```
sudo apt-get install pavucontrol sox
```

**2.** Play music or video on desktop

**3.** open pavucontrol    ```
pavucontrol
``` or from applications/sound and video

4.  Run ```
rec nameyouwant.flac
```

5.  On pavucontrol click on recording then pick "Monitor of internal audio stereo " ( or if using an external card "Monitor of whatever your external card is called") **see image**

6.  Stop recording and start again now you have the correct sound monitoring
[B]
7.  At the end [/B] make sure to return pavucontrol to original setting of "internal audio stereo"


**Your resulting file appears in home folder**

---

### Post by shantiq on 2011-07-17
===================================
===================================

**ps** if you want other formats

for lossless sound use flac above or for a thinner file ogg (112k) ```
rec nameyouwant.ogg
```

you can override settings thus

> By  default the encoding quality level is 3
              (which gives an encoded rate of approx. 112kbps), but  this  can
              be changed using the -C option (see above) with a number from -1
              to  10;  fractional  numbers  (e.g.   3.6)  are  also   allowed.


[B]example
[/B]   ```
rec   -C 9  nameyouwant.ogg

```





**OR** if you want a 128k mp3 you can add this functionality to sox thus (thanx Andrew46)   ```
sudo apt-get install sox libsox-fmt-all

```   then run ```
rec nameyouwant.mp3
```


And override this too

>   MP3 compression parameters can be selected using SoX's -C option
              as follows (note that the current syntax is subject to change):

              The primary parameter to the LAME encoder is the  bit  rate.  If
              the  value  of the -C value is a positive integer, it's taken as
              the bitrate in kbps (e.g. if you specify 128, it uses 128 kbps).
   **Example   **```
rec   -C 256 nameyouwant.mp3
```  or  ```
rec   -C 320  nameyouwant.mp3
```



other formats info **[here]("http://manpages.ubuntu.com/manpages/hardy/man7/soxformat.7.html") formats like dat cdda ircam are available if you like really high-end formats**

```
rec nameyouwant.dat
```   gives you a really heavy file of extremely good quality

---

