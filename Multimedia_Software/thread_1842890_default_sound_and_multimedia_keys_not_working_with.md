---
title: "default sound and multimedia keys not working with OSS"
date: 2011-09-12
forum: Multimedia Software
---

### Post by ab1986b on 2011-09-12
Hi All,
I have installed the latest ubuntu from live ISO on my desktop. My sound  card is Realtek HD audio with ALC 883 chipset. On the default pulse  audio and using 4.1 speakers. I have checked with keeping volume level  for all chanells including line-in high, however not got any success in  getting sound output from line-in for my rear speakers.
 Due to which I removed Pulse audio ALSAMIXER and installed OSSv4. 

OSS v4 is giving me a better performance and also with the help of my  ossxmixer I am able to get sound output from rear speakers.

However, my system default sound and my multimedia keys of keyboard is still not working.

While checking for solutions I found that I need to  install ossvol but  when I downloaded it from sourceforge.net and extracted it, I was not  able to run the file and was getting 'permission denied' error. I have  tried with root prompt and sudo command as well.

Please help me in getting my system default sound and multimedia keys working, as they were working fine with Pulseaudio.

---

### Post by dniMretsaM on 2011-09-12
Could you just set them up as normal keyboard shortcuts to do what you want? And you might need to edit the owner of the file:
```
sudo chown [your username]:[your username] /path/to/ossvol/
```

Also, the file might not be executable. The following code will make it executable:
```
sudo chmod +x /path/to/ossvol/
```

---

### Post by ab1986b on 2011-09-12
Sure!! thanx for the suggestion.. will check and revert..

---

