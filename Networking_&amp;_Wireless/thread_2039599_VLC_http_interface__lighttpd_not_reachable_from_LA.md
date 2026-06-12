---
title: "VLC http interface / lighttpd not reachable from LAN"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by codingreality on 2012-08-09
Hi all, it's me (-:

*intro*
Im in deep love with **Ubuntu 10.04** Lucid lynx with Gnome 2.x and with the same base with a enlightment dm aka Bodhi Linux 1.6.
I think theres no need to describe my network routers and so on, because the problem could be narrowed down to 10.04 Ubuntu.
Good to be here, btw GNU GNU GNU (-:
*/intro*

*problem*
I **cant reach** the **http interface of VLC Media Player** from my **LAN**.
And i think i took care of all VLC related things as :
- VLC is not bound to localhost, its on 192.168.x.x
- port **8080 is open**, nmap -p 8080 192.168.x.x
- I've added the client ip's imn the .hosts file.
The **same goes for** the testwise installed **lighttpd server**.
I can reach it locally, but not from my LAN
*/problem*

*hint*
And now the strange part :
From my old Windows **XP** partition on the same machine, i tested VLC 2.0 with the http interface - and **it worked** out of the box !
*/hint*

*outro*
Anybody out there that has knowledge in networks and may distinguish the network related specifics from win32(XP) to my Ubuntu Machine and may find the answer to this Problem just by flyby ?
*/outro*

Thank you very much folks, ubuntu rules btw (-:

---

### Post by codingreality on 2012-08-10
The solution was found (-:

It was the **Firestarter firewall** which was **not activ**, but had left its **traces** in the **iptables** already so that the requests from the **clients where blocked** !

bst.rgrds.me.out (-:


p.s. if ure looking for a fun to play game for Ubuntu, u should chk out : worldofpadman.com (-:

---

