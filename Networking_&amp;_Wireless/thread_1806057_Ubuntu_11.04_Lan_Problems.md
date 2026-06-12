---
title: "Ubuntu 11.04 Lan Problems"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by swaroopjain on 2011-07-17
Hello,
      im a newbie to ubuntu.i just have installed 11.04.i was using ubuntu 10.10 to connect with my windows 7.
when i was connecting 10.10 with win7.i did above procedures(Im using dell 4010 lap top)

1_gave 192.168.10.5 as  win7 pcs ip
2_gave 192.168.10.6 as ubuntu 10s ip adress.
3_shared some folders in ubuntu
4_by typing \\192.168.10.6 in win7s adress bar,i was able to enter the shared files on ubuntu.

but now i cant not enter ubuntu from win7.please help urgently.i really dont know what is the problem.help me.thanks in advance :-)

---

### Post by jmoorse on 2011-07-17
> **swaroopjain said:**
> Hello,
      im a newbie to ubuntu.i just have installed 11.04.i was using ubuntu 10.10 to connect with my windows 7.
when i was connecting 10.10 with win7.i did above procedures(Im using dell 4010 lap top)

1_gave 192.168.10.5 as  win7 pcs ip
2_gave 192.168.10.6 as ubuntu 10s ip adress.
3_shared some folders in ubuntu
4_by typing \\192.168.10.6 in win7s adress bar,i was able to enter the shared files on ubuntu.

but now i cant not enter ubuntu from win7.please help urgently.i really dont know what is the problem.help me.thanks in advance :-)

I don't understand. 4_ says you are able to access Ubuntu samba shares from Windows, can you try re-explaining your main problem?

---

### Post by swaroopjain on 2011-07-19
i can see the shared files of ubuntu from windows pc.but i cant enter to the folders!Im also installed samba for sharing the datas.

---

### Post by tommpogg on 2011-07-19
I suppose that you have two different PC, one with Ubuntu the other with Win7. Right?

Which partition types are you using on the Ubuntu PC? etx3/ext4?
I find quite strange that you can even see some Ubuntu folders using Win7.

---

### Post by swaroopjain on 2011-07-19
yes i have win7 pc and ubuntu 11.04 lap..im using ex4 file system on ubuntu....also when login from ubuntu by typing smb://192.168.10.5 i can see a login prompy but it wont allow me to enter win 7 eventho i entered correct uname annd password

---

### Post by tommpogg on 2011-07-19
Well, as far as I know Windows cannot recognise ext4 partitions.
I am not sure if Win7 can do that.
Anyway, you will probably need some additional software to access your ext4 file system. 

Honestly, I have never tried anything like that before, but I have found [this post]("http://www.linuxquestions.org/questions/linux-newbie-8/read-write-ext4-partition-from-windows-7-a-799039/") that can helps you.

---

