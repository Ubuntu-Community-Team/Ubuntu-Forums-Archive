---
title: "a network that can be seen but not fully used (large read)"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by SObailey on 2009-07-02
Hello Ubuntu world, I've been a long time viewer but this is my first time asking a question. So Please bare with me. I'm also not well versed in computer language( thats probably why I've just viewed).
   I have a fairly large Network that is not working right. All linux machines are using Samba.  All the computers can see each other but only one(hp a1720n running PCLinuxOS 07)can interact with all the rest. The 2nd computer(emachine 2.5GHz running Windows XP with all the updates)can see all and interact with only the PCLOS, DNS 323 storage,  HP 7920 running Ubuntu 5.04 & a Itronix laptop running XP Pro with all the updates and is the only wireless (d-link). The laptop sees and interacts just like emachine. Here's where the trouble starts. Neither of the  XP's  can interact with the Compact 1.86GHz running Ubuntu 8.04. Both the 5.04 & 8.04 Ubuntu's  can see the other computers(0 bytes) but can not interact with them including each other. The workgroup is set the same to all and sharing is set up as well There are no passwords. At one time the 5.04 could interact but no longer can( out of date I suppose can't get updates any more). Oh the 5.04 has a MySQL database which all computers can interact with using an IP address through a DIR 625 router this is our business and is backed up fortunately. Can not connect using the other computer IP addresses and can only see the database on the 5.04. Still do not want to lose the database that is why I haven't upgraded that computer but that will be another story hopefully sooner than later, All computers have internet running through the router & a Netgear DS108 hub. Well there it is in a nut shell hope some one out there can help. Also I've read a lot of forums most of witch talk about Passwords, sharing, wireless, internet  or Ubuntu 9.04 so sorry if this is a repeater. Just tired of searching.

---

### Post by swerdna on 2009-07-03
This is far too complex for a single mind to attempt to grapple with long distance, all at once. I think there are two XPs. I suggest we get one Linux computer to see and interact with the windows machines. Then when you're happy with that trio working OK, I suggest we focus on another Linux computer and get that to work well with the trio. And so on. So what about we adjust "the Compact 1.86GHz running Ubuntu 8.04" first. Can you post here the contents of the Samba config file which you can view with this command in a terminal: gedit /etc/samba/smb.conf. That will open it in a text viewer where you can copy/paste it back here.

Also, what's the name of the workgroup as seen in windows machines? (R-click My Computer --> Properties --> Computer Name --> workgroup name)

And you said PCLinuxOS was pretty much OK,, so lets have a look at its smb.conf too, just for background reference.

So that's 3 pieces of info, please, as a start.

---

### Post by superprash2003 on 2009-07-03
ok lets start with basics.. are all machines able to ping each other by ips? do you feel there could be a possibility of a firewall blocking ?

---

### Post by SObailey on 2009-07-06
> **swerdna said:**
> This is far too complex for a single mind to attempt to grapple with long distance, all at once. I think there are two XPs. I suggest we get one Linux computer to see and interact with the windows machines. Then when you're happy with that trio working OK, I suggest we focus on another Linux computer and get that to work well with the trio. And so on. So what about we adjust "the Compact 1.86GHz running Ubuntu 8.04" first. Can you post here the contents of the Samba config file which you can view with this command in a terminal: gedit /etc/samba/smb.conf. That will open it in a text viewer where you can copy/paste it back here.Ok on the PCLinux Machine. What is it I need to do to get smb.conf at a term.

Also, what's the name of the workgroup as seen in windows machines? (R-click My Computer --> Properties --> Computer Name --> workgroup name)

And you said PCLinuxOS was pretty much OK,, so lets have a look at its smb.conf too, just for background reference.

So that's 3 pieces of info, please, as a start.

Hello swerdna, Sorry didn't expect a reply so fast I've been away from the computer. I went to a terminal as you said although I'm not sure what it is you want me to copy/paste back. I'm guessing anything after a semi-colon? 2nd the workgroup for the XP machines, the storage device and the linux machines is FREEDOMENT.As for the third 3rd I'll have to log out and got to the other computer.and send it from there.

---

### Post by swerdna on 2009-07-06
If you type this (gedit /etc/samba/smb.conf) in a terminal and then press eneter, you'll get a page opening up that contains the text in the file smb.conf. You can use your mouse to block the contents and then use copy/paste to post the contents back here into a forum reply.

---

### Post by SObailey on 2009-07-06
tried copy/paste I'm missing something but have to run thanks for the help I do appreciate all the help I can get but plate is full again

---

