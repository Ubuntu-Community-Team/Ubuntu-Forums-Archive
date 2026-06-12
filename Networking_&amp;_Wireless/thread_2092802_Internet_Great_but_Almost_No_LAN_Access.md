---
title: "Internet Great but Almost No LAN Access"
date: 2012-12-08
forum: Networking &amp; Wireless
---

### Post by rlsj on 2012-12-08
Here is my sad tale from the beginning.
 

 The camel's back finally broke with Windows Vista, so I threw it out and installed Ubuntu 12.04.1 LST three days ago.  Everything worked fine, including Internet access, until I tried to access the other machines on my home network.
 

 The hardware on this machine (ex-Vista) is an Acer Aspire laptop, five years old, 1.2 GB RAM, 120 GB harddrive.  It is Ethernet connected to a multiport switch to which the other machines, three running Windows-XP and one running Debian Linux, are networked, also by wire.  The switch connects to a router that can supply IP addresses via DHCP,  which in turn connects via a broadband modem to the Internet.  Most of the machines on the LAN, including this laptop, have fixed IPs.  Note that this machine accessed the LAN perfectly under Vista, so all the hardware works.
 

 I want to transfer files freely around my network, as I did before.  Would prefer to use graphical means, with Ubuntu's Home Folder taking the place of Windows Explorer.  When I click &#8220;Browse Network&#8221; under Home Folder, however, the results vary all over the place, from no access to partial access to (once) access down to individual files.  Typically now when I click &#8220;Browse Network&#8221; I get two icons: my (networked) printer and one labeled &#8220;Windows Network&#8221; -- although occasionally even that operation fails.  Double-clicking &#8220;Windows Network&#8221; may fail or may give me an icon representing my workgroup, &#8220;localan.&#8221;  If I get to click &#8220;localan&#8221; it more often fails but sometimes will give me icons representing the machines on my network.  Clicking one of them has once shown me its files and allowed transfer to and from.
 

 Failure at any level starts typically with a box displaying,


```
Opening "<sharename>" (or "<workgroup>") 
 You can stop this operation by clicking cancel.

```                                  This appears 8-10 seconds after clicking the share icon.  Very rarely does anything good happen after that!
 

 100 or more seconds later one of the following appears,
 

                             ```
Unable to mount location 
 Failed to retrieve share list from server

```or

                          ```
The folder contents could not be displayed. 
 Sorry, could not display all the contents of "<sharename>": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```                                  Or to a &#8220;localan&#8221; click,
 

                             ```
Unable to mount location 
 DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered

```                                  --
 

 I've been researching this for a couple days, reading How-Tos and discussing it in chat.  After setting /etc/samba/smb.conf workgroup to localan, I installed and configured Samba with no discernible effect, at least no improvement using the Home Folder.  I didn't try to exercise it using the command line.  Installing &#8220;wicd&#8221; resulted in no Internet access.  Fortunately I was able to reinstall Network Manager!
 

 This might be some kind of driver problem, but I can't find out how to get the adapter type.  For what it's worth, the Network Manager says my driver is &#8220;forcedeth.&#8221;  Does Ubuntu have an equivalent to Windows' &#8220;System Hardware&#8221; dialog?
 

 Accessing the other machines is a firm requirement, and desperation time is approaching.  I still have the Vista installation disk.  Maybe a clean re-install would solve my networking problems at least.  But I hate to do it.  Vista is such a pig!
 

 Thank you for your attention.  Any suggestion will be appreciated!
 

 --Robert Smith

---

### Post by ahallubuntu on 2012-12-08
Instead of browsing, try a direct "Connect to Server" and type in the IP address of one of the machines.  I'm not that familiar with Unity or 12.04, but I'm sure you can find that dialog.  The "Service Type" is Windows Share.  Put in the IP address in the "Server:" box.  Leave the domain name blank.

---

### Post by BertN45 on 2012-12-08
"Connect to Server" is in the file menu of Nautilus, shown as "Home Folder" on the launcher. That file menu is displayed in the top bar as soon as you go there with your mouse.

---

### Post by rlsj on 2012-12-09
That works with no delays!  Thank you, [ahallubuntu]("http://ubuntuforums.org/member.php?u=32392") for the idea and [BertN45]("http://ubuntuforums.org/member.php?u=1276368") for the location.  Now I believe I can stay with Ubuntu.  Although ...  When I changed earlier from DHCP to static IP, "Browse Network" suddenly seemed to work perfectly -- until the next boot.  Now I recognize it as a coincidence, so let me try another boot this time.

Currently, despite the success with "Connect to Server," clicking "Browse Network" remains every bit as recalcitrant.  I'd like to avoid the necessity of inserting an IP address each time.  Guess I'll try putting a name in /etc/hosts.  But, really, shouldn't "Browse Network" browse?   This is a "solid intermittent" failure.  If any Ubuntu debugger would like to work with me on attacking it, my email address is [email]rlsj99@gmail.com[/email].

---

### Post by BertN45 on 2012-12-09
If you have the remote folder displayed, you can bookmark it and next time you only have to click the bookmark.

---

### Post by rlsj on 2012-12-10
Thanks to both repliers!  What you suggested results in fast and consistent results.

But isn't this in the nature of a workaround?

--Robert Smith

(I would mark this "solved" -- it's close enough -- except I don't know how.)

---

### Post by ahallubuntu on 2012-12-10
If you have three computers on your network with shares, bookmark each of them after "add to server" finds it.  You might call it a work-around - but if it works, why keep worrying about it?

I tend to blame Windows for issues like this, even though you are having the problem with Ubuntu.

---

### Post by xombie on 2012-12-10
This is an upstream problem with Gnome. Nautilus and gvfs have problems with networking and numerous bug reports have been filed with little response from the developers.

I have one smb/ftp server on my network and it takes about five minutes for my Ubuntu client to find it after reboot. I have Win7 in virtual-box and it finds the server immediately. After I close the Win7 client Nautilus will list it until I reboot the Ubuntu client.

The Linux Mint team is not happy with Nautilus and have forked its own file manager called Nemo. I hope they can fix the networking short comings.

---

### Post by rlsj on 2012-12-11
[FONT=Courier 10 Pitch]If any Ubuntu debugger is monitoring this, here is a clue:[/FONT]
 

 [FONT=Courier 10 Pitch]In the window opened when “Home Folder” is clicked,[/FONT]
 

[FONT=Courier 10 Pitch]When     a previously saved bookmark to a share, “dmed,” on the Windows     machine is clicked, after about 100 seconds the following dialog box     appears:[/FONT]
                                   
```
The folder contents could not be displayed. 
 Sorry, could not display all the contents of "<sharename>": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```                          [FONT=Courier 10 Pitch]

I have set IP 192.168.1.2 into /etc/hosts as “bigk.”  When “File”     is pulled down to “Connect to Server” and “bigk” is inserted     as the Windows Share name, after a few seconds at the top of the     dialog box an orange bar appears containing
[/FONT] 
```
Failed to retrieve share list from server
```[FONT=Courier 10 Pitch]

Again,     when “File” is pulled down to “Connect to Server” and     192.168.1.2 is inserted as the Windows Share name, in less than a     second all the share subfolders appear.  In other words, behavior is     as expected.[/FONT]  

                          [FONT=Courier 10 Pitch]These results are consistent after every reboot.  I submit that the problem is located in the code that resolves the share IP.[/FONT]
 

 [FONT=Courier 10 Pitch]--[/FONT]
 

 [FONT=Courier 10 Pitch][ahallubuntu]("http://ubuntuforums.org/member.php?u=32392") wrote,[/FONT]
                                     > I tend to blame Windows for issues like this, even though you are having the problem with Ubuntu.[FONT=Courier 10 Pitch]Sorry, I cannot agree.  This function works only when the numeric IP is supplied, but then it works perfectly.  Hmm.  Are you suggesting that Ubuntu is using something from Windows to resolve the sharename?  If so, clearly that is the mistake![/FONT]
 

 [FONT=Courier 10 Pitch]x[ombie]("http://ubuntuforums.org/member.php?u=42444") wrote,[/FONT]
                               > [FONT=Courier 10 Pitch]I have one smb/ftp server on my network and it takes about five minutes for my Ubuntu client to find it after reboot. I have Win7 in virtual-box and it finds the server immediately...[/FONT]
                                    [FONT=Courier 10 Pitch]Thank you for that observation.  It comforting when someone else experiences the same problem, proving that it's not just a failure on my part to understand the scanty and misleading Ubuntu documentation.  At least I can say about Ubuntu's documentation that it is no worse than Microsoft's.[/FONT]
  
--Robert Smith

---

### Post by dannyboy79 on 2012-12-11
check this out [http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

---

### Post by redmk2 on 2012-12-11
> **dannyboy79 said:**
> check this out [http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

[SIZE="2"][CENTER][COLOR="Red"]**Do not add winbind.**[/COLOR][/CENTER][/SIZE]

Winbind is for mapping Linux users to Windows AD.  It is not used for SMB/CIFS sharing.  The problem here seems to be name services.  Samba internally (via nmbd) maps hostnames to NETBIOS names or you can set the NETBIOS name of any Ubuntu/Samba host and bypass the hosts/DNS convention.  Either way is fine and is needed to browse shares and connect via either hostname or NEBIOS (COMPUTER) name.

---

### Post by redmk2 on 2012-12-11
> **rlsj said:**
> 
                                                                 [FONT=Courier 10 Pitch]Thank you for that observation.  It comforting when someone else experiences the same problem, proving that it's not just a failure on my part to understand the scanty and misleading Ubuntu documentation.  At least I can say about Ubuntu's documentation that it is no worse than Microsoft's.[/FONT]
  
--Robert Smith

Use the Samba documentation at [**_[COLOR="Blue"]samba.org [/COLOR]_**]("http://www.samba.org/samba/docs/").  It's much more detailed and accurate.  I recommend [URL="http://www.samba.org/samba/docs/man/Samba-Guide/"]**_[COLOR="Blue"]Samba3 by Example[/COLOR]_**
[/URL]

We can get some diagnostic information with ```
smbtree -d3
```
You should use the Samba users password but it's not specifically needed.

If you want to dump this to a file do this```
smbtree -d3 >smbtree.txt
```

Post it back here.

---

### Post by ahallubuntu on 2012-12-11
> **rlsj said:**
> ahallubuntu wrote,[/FONT]
                                     [FONT=Courier 10 Pitch]Sorry, I cannot agree.  This function works only when the numeric IP is supplied, but then it works perfectly.  Hmm.  Are you suggesting that Ubuntu is using something from Windows to resolve the sharename?  If so, clearly that is the mistake![/FONT]


Yes, that is what I am saying, and that is not a mistake.  On a Windows network, Ubuntu acts like a Windows client.  If you aren't on a domain, the way that works is that one machine on the Workgroup  acts as a "master browser."  It keeps track of what machines are on the Workgroup:

[http://scottiestech.info/2009/02/14/how-to-determine-the-master-browser-in-a-windows-workgroup/](http://scottiestech.info/2009/02/14/how-to-determine-the-master-browser-in-a-windows-workgroup/)

As you can see from that article, even Windows machines sometimes have trouble browsing in workgroups.  That's why I tend to blame Windows for problems like this.

---

### Post by rlsj on 2012-12-11
Dannyboy79's suggestion almost fixed it -- 90%!

His referenced article recommended changing a line in the file, /etc/nsswitch.conf.  The "hosts:" line in my file was of this form,

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4
```All I did to it was reverse the order of "dns wins" to "wins dns."  Eureka!  Indeed order does matter.

Now "Browse Network" works as it should, and bookmark references invoke the proper remote folders.  The only thing that doesn't work is using "Connect to Server" to invoke a symbolic name from /etc/hosts instead of the numeric IP.  That still fails exactly as described above, orange line and all, but I can ping the symbol without error.

Thank you heartily!

I would definitely mark this problem "solved" if I knew how.

--Robert Smith

---

### Post by dannyboy79 on 2012-12-11
> **rlsj said:**
> Dannyboy79's suggestion almost fixed it -- 90%!

His referenced article recommended changing a line in the file, /etc/nsswitch.conf.  The "hosts:" line in my file was of this form,

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4
```All I did to it was reverse the order of "dns wins" to "wins dns."  Eureka!  Indeed order does matter.

Now "Browse Network" works as it should, and bookmark references invoke the proper remote folders.  The only thing that doesn't work is using "Connect to Server" to invoke a symbolic name from /etc/hosts instead of the numeric IP.  That still fails exactly as described above, orange line and all, but I can ping the symbol without error.

Thank you heartily!

I would definitely mark this problem "solved" if I knew how.

--Robert SmithI am glad I could help, within that thread you may have noticed that I was telling them they didn't need winbind IF they just added hosts entries for all their static IPs as well as made sure your samba server was the master browser etc etc. I am glad you got it sorted out.

---

### Post by dannyboy79 on 2012-12-11
> **redmk2 said:**
> [SIZE="2"][CENTER][COLOR="Red"]**Do not add winbind.**[/COLOR][/CENTER][/SIZE]

Winbind is for mapping Linux users to Windows AD.  It is not used for SMB/CIFS sharing.  The problem here seems to be name services.  Samba internally (via nmbd) maps hostnames to NETBIOS names or you can set the NETBIOS name of any Ubuntu/Samba host and bypass the hosts/DNS convention.  Either way is fine and is needed to browse shares and connect via either hostname or NEBIOS (COMPUTER) name.
sorry I have to disagree with you. It clearly states, "winbindd is a daemon that provides a number of services to the Name Service Switch capability found in most modern C libraries, to arbitrary applications via PAM and ntlm_auth and to Samba itself."

---

### Post by redmk2 on 2012-12-11
> **dannyboy79 said:**
> sorry I have to disagree with you. It clearly states, "winbindd is a daemon that provides a number of services to the Name Service Switch capability found in most modern C libraries, to arbitrary applications via PAM and ntlm_auth and to Samba itself."

I'm not going to argue the point.  It's not my machine or thread.

I can tell you that from experience and understanding it will cause problems down the road.  You should not alter the NSS without completely understanding what it does.  Read up on what winbind actually is for.

That being said the is a C module that touches on name services, but that is not its primary function.  The primary functions can interfere with networking name services down the road.

---

