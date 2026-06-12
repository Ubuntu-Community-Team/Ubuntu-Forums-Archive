---
title: "Issue with easyMP3Gain"
date: 2012-10-14
forum: Multimedia Software
---

### Post by unknown user on 2012-10-14
I have just downloaded easyMP3Gain to try and normalize the volume of a number of songs that I have, so that I do not have to keep turning up or down the IPod volume.

It seemed to work the first time and all went well. However, when I come to add files to it the second time, it does not select them. I cannot select any files or even close down the application. All I can do is kill the process that is running around 96% of CPU.

Has anyone come across this and know how to sort it out?

---

### Post by unknown user on 2012-10-14
It would appear that this is a known issue with the application. I have had a search on the net today and I have been able to find this site that describes fixes for the freezing/ crashing:

[https://bugs.launchpad.net/ubuntu/+source/easymp3gain/+bug/875878](https://bugs.launchpad.net/ubuntu/+source/easymp3gain/+bug/875878)

Looks like post number 9 is the one. As yet I have not had chance to try it, but when I do I will post the results.

---

### Post by unknown user on 2012-10-15
Today I tried this, but I got a little stuck at the following point:

go to the download dir, normally Downloads:

cd Downloads

sudo dpkg -i easymp3gain-gtk2_0.5.0-2_i386.deb

I opened the file, but it did not do anything. Also in this line (sudo dpkg -i easymp3gain-gtk2_0.5.0-2_i386.deb) do I need to add the path of where the download is, to make it work?

Can anyone help with this?

---

### Post by unknown user on 2012-10-16
Well gosh, as it stands 151 people looking at this post and not one person can give any help on this issue. Can I be the only person that is using this program or who has had this issue? I do not think so, but after 151 views, it may seem so.

Oh well, life goes on. For all the people who are using this and are interested, I have found a way around this. not a fix, just a viable work around. When you get the file selection box and it all seems to freeze, move down to any corner of the box and resize it. This way you will then be able to get the scroll up and down arrows in the selection box. This seems to bring the whole system back to life so that you can select the files you want and normalize them. I have only tried this with a single file selection at the moment, but if it only works with this, it is better than nothing :)

---

