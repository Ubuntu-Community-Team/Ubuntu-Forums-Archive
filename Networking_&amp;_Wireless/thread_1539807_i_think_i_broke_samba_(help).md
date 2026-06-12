---
title: "i think i broke samba (help?)"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by lisarox on 2010-07-27
so i've been using ubuntu for like 4 months , and worked my way through most issues (mostly by searching here:D)


i had some trouble setting up samba but eventually it worked out fine . now suddenly whenever i try to open a shared folder it gives me this message :**Failed to retrieve share list from server** (and that is after waiting like forever while it says like "hey ,you wanna cancel?":()
so yeah i have no idea what's wrong or what caused this

however ; i found [this thread]("http://ubuntuforums.org/showthread.php?t=1539516&highlight=samba") so i thought i should change my dns as they said , by adding this : **prepend** **domain-name-servers <my router ip>**  here [B] /etc/dhcp3/dhclient.conf
[/B]restart  and..nothing:(

and now it won't even give me a list of computers on the network , just shows a folder called WORKGROUP (which is the name of the work group other pc's on the network run on (they all run windows)

now in order to do anything network related i have to reboot into windows , and i hate windows:(
so , any suggestions?

---

