---
title: "Yes! Once again: ATI Radeon 9200 Mobility"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by Kosmonaut on 2006-06-26
Hi freaks!

I know that there are many threads dealing with the ATI driver....But unfortunatly I was never able to get this "fglrx" driver to work reliably. So I thought that I should go back to the "radeon" driver.
I followed the instruction that I found at the ubuntu wiki: [https://wiki.ubuntu.com/RadeonDriverHowto?highlight=%28driver%29%7C%28radeon%29]("https://wiki.ubuntu.com/RadeonDriverHowto?highlight=%28driver%29%7C%28radeon%29") but without success. There is still no 3d acceleration enabled!

Ich@Diabolo:/usr/lib$ glxinfo | grep "direct rendering"
direct rendering: No

The "funny" thing about it is, that with kubuntu-live.CD "direct rendering" is working!
So here ist my questions:
1. How can I enable "radeon" so that I have 3D?
2. What files should I copy from the LIveCD (into my installed Kubuntu), to enable "radeon"?
3. Finaly: Is "radeon" working for you. Or am I the only one having this trouble?

---

### Post by ajgreeny on 2006-06-26
Interestingly, I don't even get the option of a radeon driver if I do sudo dpkg-reconfigure xserver-xorg, but I do get the ati driver which works well for me.  I've also tried many times with dapper to get the 9200 working (not mobility) but given up for now; it's just too much hassle.

---

### Post by Kosmonaut on 2006-06-29
Ok...I still have not figured out what the problem could be, maybe there is a guru out there, knowing a little ;-) more linux hacking than me, who could help me out.
Attached is a screenshot of my 2 glrxinfos logs with the same xorg.conf (->Driver "ati". that does 3D rendering with my Live-CD) 
A: Installed Kubuntu (no 3d rendering) 
B: Live-CD Kubuntu (3d rendering).
So as you see there is a difference, but what do I do next?

PS: I have reinstalled all kind of xorg/libGL.so.1/mesa stuff out there but without success.
PPS: As allways sorry for my english #-o

---

### Post by Kosmonaut on 2006-07-03
*bump*

---

### Post by Craig Watson on 2006-07-04
I have a working radeon 9200 (not mobility) (well more or less), it works fine with 3D OR with multidisplay with the "radeon" driver. If you want my xorg.conf (it probably won't be any help.. but you can try all the same.. have a look [here]("http://ubuntuforums.org/showthread.php?t=207911") (and hopefully you can help ME out ;) )

---

### Post by Kosmonaut on 2006-07-09
I still haven´t found out, what my problem could be.
But I still hope that maybe someone can help me out.

As I said before, with the Live-CD 3D works fine. 
1.So I´m wondering how to configure the x-server so that it is set-back to it´s original version.
2.When I tried to install the fglrx driver i followed this [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")
I also used "method2"...I wondering how to "reset" the kernel, because I guess that my problem is a rest-existing fglrx module.
3. Hope you folks understand my english after all :-)

---

