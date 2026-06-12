---
title: "Split video stream across multiple N/W interface"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by neosrix on 2010-09-15
I want to do a video streaming to a remote PC across the internet. The video bitrate is around 600 kbps. But my internet connection supports only a maximum upload bandwidth of 400 kbps.

So I thought I will get one more connection and use the combined upload b/w of 800 kbps to stream the video. I hope there should be a way to split the stream across two interface and merge them together at the remote endpoint. All this has to be done at real time. 

Is SCTP a right candidate? Please let me know how to do this.

---

### Post by neosrix on 2010-11-22
Well after a month of research, I found out that its an age old concept called NIC bonding. you can achieve the bandwidth split by setting the NIC bonding in Round Robin mode. NIC bonding also supports few other mode. the Following links provide more information.


[Linux bond or team multiple network interfaces (NIC) into single interface]("http://www.google.com/url?sa=D&q=http%3A%2F%2Fwww.cyberciti.biz%2Ftips%2Flinux-bond-or-team-multiple-network-interfaces-nic-into-single-interface.html")

[Linux Ethernet Bonding Driver HOWTO]("http://www.google.com/url?sa=D&q=http%3A%2F%2Fwww.cyberciti.biz%2Fhowto%2Fquestion%2Fstatic%2Flinux-ethernet-bonding-driver-howto.php")

[https://help.ubuntu.com/community/UbuntuBonding]("http://www.google.com/url?sa=D&q=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FUbuntuBonding")

[NIC bonding with Lucid/Maverick]("http://www.google.com/url?sa=D&q=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1596696")

</span>

---

