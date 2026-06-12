---
title: "Error - Unable to mount location: Failed to retrieve share list from the server"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by dave8513 on 2010-05-16
Upon browsing my Windows network via Places > Network > Windows Network in Ubuntu 10.04, I receive the following error:

**Unable to mount location**
Failed to retrieve share list from the server

I used to use Ubuntu 9 on this machine until I recently wiped and installed 10.04 (both installs via Wubi). Ubuntu 9 had absolutely no problems whatsoever - same exact hardware, drivers, etc.

Firewall isn't the problem because it still gives the error even when the firewall (ufw managed with gufw) is disabled.

Attempted to perform Fix #3 in [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149) to no avail.

I'm sure there is plenty of material available on this problem in general, but I'm not sure what's out there for Ubuntu 10.04. This seems especially odd since it worked fine with Ubuntu 9.

---

### Post by cariboo on 2010-05-16
Have you set a samaba password? IF you haven't, open a terminal and type:

```
sudo smbpasswd -L -a <user>
```

then to enable the password:

```
sudo smbpasswd -L -e <user>
```

where <user> = your user name.

---

### Post by Iowan on 2010-05-16
Some time ago, I did a search for the error message:```
Error - Unable to mount location: Failed to retrieve share list from the server
```there were too many responses to provide links, but the problem could be accessibility or connectivity. You can ping the machine (name/IP address)?

---

### Post by dave8513 on 2010-05-17
> Have you set a samaba password?I believe that I  had already tried this.

No luck, but I do receive a different  error message when accessing "Windows Network:"

```
Unable to  mount location
DBus error
org.freedesktop.DBus.Error.InvalidArgs:
Mountpoint  Already registered
```Once there, I cannot get into the  "WORKGROUP" part (all computers are on workgroup "WORKGROUP," including  this one. When I try, I receive the original error message.

> You  can ping the machine (name/IP address)?Yes, with typing

```
smb://rog-office1/
```into nautilus  (rog-office1 is a Win XP computer). I can view all files on this share.

This  is an improvement. Thank you guys!

However, as of right now,  when I load the "Windows Network," it works for a couple of seconds and  then shows up blank. No "WORKGROUP" as there should be.

Any more  ideas?

---

### Post by dave8513 on 2010-05-19
Can anybody help?

---

### Post by kwalters on 2010-05-20
Sorry I cannot help. But you might like to know that I am having the same problem. I have been with Ubuntu since version 7.04 and have never had any problem connecting Ubuntu and Windows machines together  -  until, that is, I installed 10.04

I have followed innumerable threads on this forum; and I have typed more text into a terminal than Shakespeare produced in his lifetime.  But I cannot even connect with my NAS hard drive.  Ubuntu machines can see it, but give the perennial error message about retrieving share list from server. Ubuntu machines can see each other, but give the same error.  Windows machines work and see the NAS as they always have.

I am going to spend one more weekend following threads on the same subject (and there are lots of them) then I am going back to version 9.10; what an indictment of the new system.

KWalters    :(

---

### Post by dave8513 on 2010-05-20
> **kwalters said:**
> Sorry I cannot help. But you might like to know that I am having the same problem. I have been with Ubuntu since version 7.04 and have never had any problem connecting Ubuntu and Windows machines together  -  until, that is, I installed 10.04

I have followed innumerable threads on this forum; and I have typed more text into a terminal than Shakespeare produced in his lifetime.  But I cannot even connect with my NAS hard drive.  Ubuntu machines can see it, but give the perennial error message about retrieving share list from server. Ubuntu machines can see each other, but give the same error.  Windows machines work and see the NAS as they always have.

I am going to spend one more weekend following threads on the same subject (and there are lots of them) then I am going back to version 9.10; what an indictment of the new system.

KWalters    :(

The odd part is that I can even ping the machine. Can you ping the machine at all? Can you try using the SMB command that I typed earlier? Type this into nautilus:

```
smb://COMPUTER-NAME/
```Where obviously COMPUTER-NAME is the name of a computer or device you are trying to access (can also be an IP address).

Clearly the problem has to be on either the Ubuntu machine or some configuration on the Windows machine that Ubuntu doesn't like. What version of Windows are you using?[]("http://ubuntuforums.org/showthread.php?t=1082148&highlight=Failed+retrieve+share+list+server&page=2#18")

---

### Post by dave8513 on 2010-05-21
Bump

---

### Post by dave8513 on 2010-05-23
Bump

---

### Post by buadhai on 2010-05-23
The only thing I had to do to get this to work was change this line:

[SIZE=2]   name resolve order = lmhosts wins bcast host

in smb.conf
[/SIZE]
Once I did that the workgroup, which I could always "see", became browse-able.

---

### Post by dave8513 on 2010-05-25
I have already tried this fix as well, where one switches (or adds, I can't remember which) the "wins" part to be

```
name resolve order = lmhosts wins bcast host
```in /etc/samba/smb.conf.

I did not have the "lmhosts" option, though. I change my line to be exactly as you said and rebooted. No luck. Same old

```
**Unable to mount location**
Failed to retrieve share list from the server
```error. :(

Any other ideas?

**Edit:** Added my smb.conf file for anybody who needs it.
**Edit:** It is also worth noting that I can successfully mount my shares permanently (with guide at [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)). However, everything is READ-ONLY. To me, everything in this case seems to point to some sort of authentication issue, by I am not sure what it could be...

---

### Post by dave8513 on 2010-05-26
Bump

---

### Post by dave8513 on 2010-05-31
Bump

---

### Post by rod40cool on 2010-06-02
I was having the same thing, but it turned out for me that my firewall is blocking SAMBA which was causing this error. 
Maybe you have UFW turned on or Firestarter loaded.

If i switch off UFW using ```
sudo ufw disable
``` browsing works again and I can browse the WORKGROUP and the Windows domain at work.

I am still researching to find the work around which appears to be adding exceptions in the firewall rules to allow SAMBA protocols. [Found this bug]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/474020") relating to firewall and SAMBA.

I hope this helps you.

Cheers :)

---

### Post by dave8513 on 2010-06-03
Hmm...odd. I can browse the network now, but I can't see any computers in the "WORKGROUP" workgroup...which all of the computers are in.

Well, that partially solved the problem. But why can't I see the Windows computers? (No error messages.)

---

### Post by brain_stergeon on 2010-06-03
I think it is an update related issue as I have been using 10.04 for the last week or so and have had no problems at all until it updated and now I get the same error as mentioned earlier. Either way it is rather annoying when things just decide to stop working.

---

### Post by NoVista on 2010-07-28
Yes, it was due to updated packages. (for me).
The firewall was the culprit. But why?
I never changed a thing.

This got it working for me, switching off UFW.
Now the WORKGROUP name will show up.

Thank You.
Wish I knew what updated packages were responsible for the system to suddenly be unable to show the WORKGROUP name, but I don't.

---

### Post by backwards on 2010-08-06
Same here. "sudo ufw disable" now all appear. Last weekend I was streaming music from my NAS. Monday I shared files with another machine and ran updates before shutting down. Thursday night network was gone.

Happy days again Thanks Rod40cooooool!

---

### Post by raceon4 on 2010-08-11
I am totally lost on this one as well.  I have read so many things I'm not sure what to do.  I can see the workgroup group but can't get into it.  I did disable UFW. Any other options?

---

### Post by keithspg on 2010-08-24
Totally and completely sucks!!!! What is going on? I can browse 'my' shares, but I cannot browse any other shares on the network. I have no problem 'connecting' to shares this when I am local or even vis VPN. From the command line all appears fine with smbclient -L, etc. I just cannot browse anything in nautilus. May also be linked to the fact that I cannot browse any obex either. please help.

---

### Post by PerryCS on 2010-09-27
I have been having this problem for ages even across different versions of Ubuntu.   It's a very odd problem.   When I first installed the Ubuntu 2 generations ago :) it worked... then one day after weeks of working.. it stopped.  It would connect to windows shares intermittantly.  Then poof - start working again.   

Then I upgraded to Ubuntu 9.  It was nice.   Same problem.  Worked for a while, then stopped.  If I rebooted a few times it would sometimes connect to windows shares.  Some days I would give up.

Then I upgraded to 10.04 LTS.  Worked great in the beginning then withing a few days stopped working again.  Rebooting sometimes solved it but after a while it never connects anymore.  For months now to get connected I have to type...

sudo mount -t cifs //gaming1/Enjoyment /mnt/gaming1share1

Then it works 99% of the time.   In the past I was able to browse through the windows shares in the GUI AFTER connecting that way.. it would "poof". all of a sudden work.


Now - for clarity.   During ALL this...   every machine is pingable.   All the windows machines can see each other AND all the windows machines can access the Ubuntu share BUT the Ubuntu machine can no longer get past browsing the workgroup.

In the past.. I would click... places, network and I would get "Windows Network", then PCS (my network), now.. here's where it's different...

In ver 9... if I clicked PCS I could sometimes browse the network.  Click on PCS1 (my main machine) but it would stop there sometimes - but not always.  Rebooting or trying a few times would sometimes work.  Other days, it would work 1st try.

In Ubuntu 10.04...  it worked for a while, then never worked again except through that sudo command above which by the way took me many hours of searching to find one that worked.

I have booted off live disks as a "test" only to find it too... acts odd - sometimes works, usually doesnt.  Which is weird since I used to use the Live disks to copy data off customer machines to back then up before wiping windows and reinstalling.

The error I get when it fails is the same.   

OPENING PCS.  You can stop this operation by clicking cancel.
UNABLE TO MOUNT LOCATION
Failed to retrieve share list from server.

It should show me a pile of machines...
PCS1, PCS2, GAMING1, GAMING2, ACCOUNTING, etc...



I have tried so many fixes on the web.  I have even installed Fedora and another Ubuntu on another "fooling around" machine and they both dont work either.

So...   I don't know what was screwed up.  But there is an ongoing problem with this.  Maybe the programmers have never ran into this bug.  I dont know why not.. because I have a 9 computer network of windows machines, 1 Ubuntu.  All ranging from Windows XP to Vista, to 7 32 bit and 64 bit.  They all work perfectly at all times.

I have reset my modem, router, multiple switches and nothing works anymore.   

I really hope someone one day fixes this.   Any programmers wanna come to my house and poke around on my Ubuntu machine - be my guest!  :)  Let me know, we can set a time up for you to come over since this obviously isnt going away anytime soon and it affects all Linux platforms that I have tested so far!

This bug severely hampers my fun with Ubuntu.   If I didnt WANT to learn Ubuntu - I would have scrapped it long ago!

I am a programmer from the old days (6502 asm on the C64, pascal, etc) and am currently learning more modern languages (Visual Studio 2008 C#/C++).  If anyone wants to remote control my linux box they are more than welcome.  You can even mess up the installation if you want by tinkering.  I'll just wipe and reinstall afterwards.  It's only a learning machine for me!  I'm on it right now :)

So... please fix this! :)  You want to use a machine that has the issue... go for it!  Lets get this bug fixed once and for all!

David Perry
Perry Computer Services
[www.perrycomputerservices.com]("http://www.perrycomputerservices.com")
905-999-3590
Oshawa, Ontario, Canada

---

### Post by haafmaad on 2010-09-28
@perryCS you are lucky!

I can't even ping other windows/linux machines from my ubuntu 10.04LTS.
I have disabled ufw and firestarter still no luck. I have been trying since 8.10 to access share in the LAN, NO Luck :(. I can access the lan shares easily from my windows PC.
 
The  most annoying thing is I can't access some of the websites. I have tried with many browsers like lynx, safari,opera,firefox,chrome. becoming hopeless

---

### Post by capscrew on 2010-09-28
> **PerryCS said:**
> I have been having this problem for ages even across different versions of Ubuntu.   It's a very odd problem.   When I first installed the Ubuntu 2 generations ago :) it worked... then one day after weeks of working.. it stopped.  It would connect to windows shares intermittantly.  Then poof - start working again.   

Then I upgraded to Ubuntu 9.  It was nice.   Same problem.  Worked for a while, then stopped.  If I rebooted a few times it would sometimes connect to windows shares.  Some days I would give up.

Then I upgraded to 10.04 LTS.  Worked great in the beginning then withing a few days stopped working again.  Rebooting sometimes solved it but after a while it never connects anymore. 
Interesting.  I have a fully functional heterogeneous network made up of Ubuntu and Windows OS's.  I have a Ubuntu Hardy (8.04) server (no GUI) and a Lucid (10.04) Desktop plus any number of XP and Vista machines.  The Windows hosts are laptop and white box machines.  They all work correctly.  The users can browse for shares.  In one specific instance I have mounted one of the shares on the Hardy (8.04) server to the Ubuntu desktop via the **mount -t** command in a script. 

> 
For months now to get connected I have to type...

sudo mount -t cifs //gaming1/Enjoyment /mnt/gaming1share1

Then it works 99% of the time.   In the past I was able to browse through the windows shares in the GUI AFTER connecting that way.. it would "poof". all of a sudden work.


Now - for clarity.   During ALL this...   every machine is pingable.   All the windows machines can see each other AND all the windows machines can access the Ubuntu share BUT the Ubuntu machine can no longer get past browsing the workgroup.

In the past.. I would click... places, network and I would get "Windows Network", then PCS (my network), now.. here's where it's different...

In ver 9... if I clicked PCS I could sometimes browse the network.  Click on PCS1 (my main machine) but it would stop there sometimes - but not always.  Rebooting or trying a few times would sometimes work.  Other days, it would work 1st try.

In Ubuntu 10.04...  it worked for a while, then never worked again except through that sudo command above which by the way took me many hours of searching to find one that worked.

I have booted off live disks as a "test" only to find it too... acts odd - sometimes works, usually doesnt.  Which is weird since I used to use the Live disks to copy data off customer machines to back then up before wiping windows and reinstalling.

The error I get when it fails is the same.   

OPENING PCS.  You can stop this operation by clicking cancel.
UNABLE TO MOUNT LOCATION
Failed to retrieve share list from server.

It should show me a pile of machines...
PCS1, PCS2, GAMING1, GAMING2, ACCOUNTING, etc...

This can be for a variety of errors in configuration.  The root cause is that host you are browsing on can't get the information it needs from the master browser on the LAN. 
> 

I have tried so many fixes on the web.  I have even installed Fedora and another Ubuntu on another "fooling around" machine and they both dont work either.

What testing have you done?  Have you any errors in the Samba logs?> 

So...   I don't know what was screwed up.  But there is an ongoing problem with this.  Maybe the programmers have never ran into this bug.  I dont know why not.. because I have a 9 computer network of windows machines, 1 Ubuntu.  All ranging from Windows XP to Vista, to 7 32 bit and 64 bit.  They all work perfectly at all times.

My take is: **it is NOT a bug**, but more a misconfiguration somewhere.> 

I have reset my modem, router, multiple switches and nothing works anymore.   

I really hope someone one day fixes this.   Any programmers wanna come to my house and poke around on my Ubuntu machine - be my guest!  :)  Let me know, we can set a time up for you to come over since this obviously isnt going away anytime soon and it affects all Linux platforms that I have tested so far!

The best I can do is give you advice on the results you can post here.  :-)> 

This bug severely hampers my fun with Ubuntu.   If I didnt WANT to learn Ubuntu - I would have scrapped it long ago!

I'm sure it does.> 

I am a programmer from the old days (6502 asm on the C64, pascal, etc) and am currently learning more modern languages (Visual Studio 2008 C#/C++).  If anyone wants to remote control my linux box they are more than welcome.  You can even mess up the installation if you want by tinkering.  I'll just wipe and reinstall afterwards.  It's only a learning machine for me!  I'm on it right now :)

So... please fix this! :)  You want to use a machine that has the issue... go for it!  Lets get this bug fixed once and for all!

Better yet, lets see if you can fix it with a little help.

To start with we can check the shares and NetBIOS names from a Ubuntu host with this command from the terminal```
smbtree
```

In fact you can tell a lot from this command if you up the debug level.  I would pipe this to a file for easier reading.  Try this ```
smbtree -d4 > tree.txt
```

Post the output here so we can go through it together.

A similar output is available for the terminal in **Windows**.  To see this try this:```
net view
```

Not as much information but enough to see if the Ubuntu host shows up.  Please post this output too.

---

### Post by luvshines on 2010-09-28
smbtree will surely help.

Also, you may also try this.
1. Ping the server name(as it appears on the network) - This should pass
2. Either "nc -zv <server-name> 139" OR "nc -zv <server-name> 445" should pass

I was not able to re-create this problem. But now that I have it, let's shoot it down.

Found that those which were inaccessible, either were not pingable (that's 1 step) or both 139 and 445(that's 2 step) timed out

---

### Post by godric7gt on 2010-11-14
In my case ubuntu is not able to ping itself(says destination host unreachable), or to Vista(no output), but I can ping the router. I tried this with the firewall disabled as well but to no avail. Both Vista and ubuntu are assigned IP's by the router. Can someone help, please?

Note: I can access Ubuntu shares from Vista using IP address, the name does not work.

---

### Post by PerryCS on 2010-11-14
Hey there CapScrew, thank you for your detailed response.  I forgot my password and couldn't log in for a while and I've been busy.   I did try some of your suggestions and it's cool to know what "tools" are there that I didn't know of before.  Knowledge is power :)

An odd thing happened recently.  I switched from Rogers to Distributel and in the process had to rewire my entire network.  At first it branched out from my room to the livingroom but the DSL originates in the livingroom so I wired it the "other way" towards my room.  I removed 1 8 port Dlink switch, and moved my 16 port Dell Switch (it was free) to the livingroom.  In the process I had to switch my network from 192.168.0.X to 192.168.1.X becuase the horrible DSL they sent me was ALSO a router and my Dlink Extreme would not work with a WAN and LAN on the same subnet (understandable) but after changing everything and logging into here as a joke I clicked NETWORK and POOF - ALL my network showed up fully browsable (except the Windows 7 machine but I have an idea on why that is happening).

So... a VERY weird problem solved by moving my network around and changing  my DHCP pool in my router to a different one.

WEIRD but it works!

So.. the test will be.. will it revert back in a short period of time like it has in the past.   Time will tell.

I WILL keep in touch if anything changes.

PREVIOUS NETWORK from router to Ubuntu... 192.168.0.X
Rogers Cable into DLINK EXTREME DIR655 into Linksys 8 Port Gigabit Switch  into 100ft cable into Dlink Gigabit switch, into Ubuntu machine. ...(also plugged into the Linksys GB switch is the 16 port Dlink 10/100 switch branching off into my rooms computers AND also plugged into the Dlink GB switch was an 8 port 10/100 Dlink old switch)

NEW NETWORK CONFIG... 192.168.1.X
ZHONE DSL Router (ugh) into Linksys VOIP, into DLINK EXTREME DIR655 into Dlink 8 port gigabit switch into Ubuntu.  (ALSO plugged into the Dlink gigabit switch is the 100 ft cable bridging switches and the 16 port 10/100 Dell, and in my bedroom side just the Dlink 10/100 8 port switch connected to the Linksys Gigabit switch.

I have a feeling it's more of the subnet change than anything.  The equipment is the same, just swapped around and a switch is a VERY basic device.  I can't see why Ubuntu would have problems with the # of switches between it and the router.

Well, that's what I did to solve a huge problem here.  Thought I would post it and see what happened.

Also, I noticed some interesting settings in my DIR655 relating to broadcasting NETBIOS names.  I didn't touch them but it looks like the more advanced DIR655 has "extra" options most routers don't have.  It would be interesting to see how many people having this problem use Dlink DIR 655 routers?   Just curious.

---

### Post by Rebelli0us on 2010-11-21
What's happening, I was always able to browse any machine on my home network, but not today!

I'm not complaining, I know they'll fix this eventually. This new Maverick 10.10 boots faster than anything and is very stable... so network or not MS will be ki$$ing my a$$ very soon.

---

### Post by stanley82 on 2011-04-23
I have the same problem, sort of.  I can usually mount the ubuntu shared files from No 2 computer on No 1 only when the firewall is disabled.  Once it's mounted I can read write okay with the firewall enabled.  My computer is pure ubuntu 10/4 and No 2 is mint 10/4. I've given up on my old win98 machine.  This name resolve order does nothing.

# to IP addresses
    name resolve order = lmhosts host wins bcas
;    name resolve order = lmhosts wins bcast host
;    name resolve order = hosts wins bcast

---

