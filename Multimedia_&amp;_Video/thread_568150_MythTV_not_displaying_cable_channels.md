---
title: "MythTV not displaying cable channels"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by pheno on 2007-10-05
I installed MythTV using the MythTV Feisty Backend Frontend Desktop instructions. I’m using a Hauppauge-WinTV-PVR-350 TV Tuner. I configured the backend and frontend, but when I run the frontend and select LiveTV, I get snow. The channel frequency table on the Global Backend Setup is set to “us-cable”
 
I did have problems with Mythbackend setup not saving settings and followed the instructions on the Troubleshooting page linked in the Backend Frontend Desktop instructions

I’ve never been able to view TV thru the tuner card. Is there a way to test it without using MythTV?

I have searched the forums for an answer to this...

---

### Post by jimbodude21 on 2007-10-06
If you're using IVTV, you can do it like this:

Do an "ls" to find out the deice names of your capture card, then use "cat" to capture the output to an mpeg file - like this:

```
j@jmedia:~$ ls /dev/video*
/dev/video0  /dev/video24  /dev/video32
/dev/video1  /dev/video25  /dev/video33
j@jmedia:~$ cat /dev/video0 > test.mpg
```
press CTRL+C to stop the cat command when you think you've captured enough samples, then view the video:
```
j@jmedia:~$ mplayer test.mpg
```

You can change the channel of the card at any time using this command:
```
j@jmedia:~$ ivtv-tune --device=/dev/video0 --channel=5
```
You may want to check a few different channels.

I would also try another device - like a TV - because if you're not getting any signal, you can fiddle with your system config all day and not get anywhere.

---

