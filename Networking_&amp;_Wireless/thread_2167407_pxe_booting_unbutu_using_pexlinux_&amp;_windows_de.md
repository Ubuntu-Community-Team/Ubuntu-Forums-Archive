---
title: "pxe booting unbutu using pexlinux &amp; windows deployment service 2008r2"
date: 2013-08-13
forum: Networking &amp; Wireless
---

### Post by dureal99d on 2013-08-13
I have been racking my brain for literally 2 days strait; day and night in an attempt to get ubuntu to boot using pexlinux via windows deployment services. I have gotten a little ways in that linux does go thru some of the boot code but then i get this message

 Begin: trying netboot from my (servers ip address) "the directory i set" then Begin: trying nfsmount -0 nolock - ro ([COLOR=#ff8c00]**see attached Pic**[/COLOR]) nfsmount: can't parse IP address? ([COLOR=#ff8c00]see attached pic[/COLOR]) i have no idea what this means and why my boot is locking up here

[ATTACH=CONFIG]245338[/ATTACH]

 I am stuck at the point of no return please help me i know its something i am lacking and or need to reconfigure i just cant seem to figure it out.

oh and i am using & have successfully configured syslinux version 5.01 so i can install windows vista,7 & 8 just fine from pxe boot

any help  would be greatly appreciated!!! thanks

---

### Post by newbie-user on 2013-08-13
The client seems to be getting 0.0.0.0 as its default gateway. Perhaps that's causing the problem?

---

### Post by dureal99d on 2013-08-14
gateway not needed as I am not booting to the internet? I also don't need the second dns ([COLOR=#ff8c00]dns1[/COLOR]) as my first dns (dns0) 192.168.1.2 is being noticed now.

Also i have gotten a tad bit further in that changing it to boot from nfs in this line ([COLOR=#ff0000]see red[/COLOR])

APPEND [COLOR=#ff0000]boot=nfs[/COLOR] netboot=nfs nfsroot=192.168.1.2:/Images/Ubuntu/ubuntu-13.04-desktop-amd64 initrd=/Images/Ubuntu/ubuntu-13.04-desktop-amd64/casper/initrd.lz

used to be: 

APPEND [COLOR=#ff0000]boot=casper[/COLOR] netboot=nfs nfsroot=192.168.1.2:/Images/Ubuntu/ubuntu-13.04-desktop-amd64 initrd=/Images/Ubuntu/ubuntu-13.04-desktop-amd64/casper/initrd.lz

now i get running  /scripts/nfs-premount ... done. (which i consider a step forward) however ([COLOR=#ff8c00]see screen shot[/COLOR]) the server replies with a no such file or directory. I do not understand why this is the case. I assume I have something configured wrong but I just don't know what I have wrong.

[ATTACH=CONFIG]245356[/ATTACH]

As always any help is greatly appreciated.

---

### Post by newbie-user on 2013-08-15
If your nfsroot=192.168.1.2:/Images/Ubuntu/ubuntu-13.04-desktop-amd64, then shouldn't your initrd=casper/initrd.lz?

I think it might be looking for /Images/Ubuntu/ubuntu-13.04-desktop-amd64/casper/initrd.lz inside of /Images/Ubuntu/ubuntu-13.04-desktop-amd64. As if to say the file in question is /Images/Ubuntu/ubuntu-13.04-desktop-amd64/Images/Ubuntu/ubuntu-13.04-desktop-amd64/casper/initrd.lz

---

### Post by dureal99d on 2013-08-15
Hum excellent thought, following your statement i reviewed the config file and well let me show you

[COLOR=#0000ff]kernel Images/Ubuntu/ubuntu/casper/vmlinuz.efi[/COLOR]

[COLOR=#0000ff]APPEND [/COLOR][COLOR=#ff0000]boot=nfs[/COLOR][COLOR=#0000ff] netboot=[/COLOR]Server1[COLOR=#0000ff] nfsroot=server1:/Images/Ubuntu/ubuntu initrd=/Images/Ubuntu/ubuntu/[/COLOR][COLOR=#ff8c00]casper/initrd.lz[/COLOR]

(note)I have changed the install location to make the name shorter, my boot issues maintain the same. 

casper/initrd.lz [COLOR=#ff8c00](see orange)[/COLOR] is already a part of the config, that unless i am not understanding what you are saying which is quite possible.

i also tried 1 more thing I changed (see red) [COLOR=#ff0000]boot=nfs [/COLOR]to [COLOR=#ff0000]boot=server1[/COLOR] & now I get (see pic)

[ATTACH=CONFIG]245385[/ATTACH]

---

### Post by dureal99d on 2013-08-15
OOOOOh I see what you are saying now, you are saying that somehow it continues to look for the needed boot files in the wrong folder.

Mt question is how do i get it to look in the right folder, what do you recommend?

---

### Post by newbie-user on 2013-08-17
Your line should read:

APPEND boot=nfs netboot=nfs nfsroot=192.168.1.2:/Images/Ubuntu/ubuntu-13.04-desktop-amd64 initrd=casper/initrd.lz

So what this is saying is that the nfsroot folder is on the server 192.168.1.2, at the path /Images/Ubuntu/ubuntu-13.04-desktop-amd64. Then the client mounts that location. So to the client, the folder which it finds itself in is the ubuntu-13.04-desktop-amd64 folder. Then the initrd file (initrd.lz) is within the current folder in a directory called casper.

---

### Post by dureal99d on 2013-08-17
> **newbie-user said:**
> Your line should read:

APPEND boot=nfs netboot=nfs nfsroot=192.168.1.2:/Images/Ubuntu/ubuntu-13.04-desktop-amd64 initrd=casper/initrd.lz

So what this is saying is that the nfsroot folder is on the server 192.168.1.2, at the path /Images/Ubuntu/ubuntu-13.04-desktop-amd64. Then the client mounts that location. So to the client, the folder which it finds itself in is the ubuntu-13.04-desktop-amd64 folder. Then the initrd file (initrd.lz) is within the current folder in a directory called casper.

Ok!! I will try this configuration and let you know how it works out.

---

### Post by dureal99d on 2013-08-18
Not working? :frown:

---

### Post by newbie-user on 2013-08-18
Just checking, have you correctly shared the nfsroot directory via nfs?

---

### Post by dureal99d on 2013-08-19
Yes or at least I think I have, perhaps I should try and check it from a Linux system say Ubuntu or the like ie; mint or something

---

