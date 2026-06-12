---
title: "the ever present &quot;Failed to retrieve share list from server&quot;"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by CliveMcCarthy on 2013-07-31
There are many many posts on this issue on this forum and others and I haven't found anything definitive. I experience the "Failed to retrieve share list from server" from time to time. It isn't consistent at all. Sometime things work just fine for days & days... then nothing. I reboot my router, access points and my clients then wait forever, and sometimes things get back to normal. Sometimes not.

I have a network with many Linux machines, a few Win XP machines and a Mac. When things are bad it is impossible to find shared folders EVEN ON OTHER LINUX MACHINES -- the machines just don't show up at all. If I try the "Window's Network" I can sometimes find a WORKGROUP names but they just lead to the "Failed to retrieve share list from server" message. I use a very convenient utility called which can be found at: [http://www.overlooksoft.com/download](http://www.overlooksoft.com/download) -- I have it on my phone as well as various laptop/desktop machines and it clearly identifies what machines are on my network, what their names are and their ip addresses. The utility nbtscan also finds all the machines on the network. It works all the time so why can't Nautilus?

The curious thing is that the Mac on the network is visible! I suspect that it isn't a Windows/Samba thing but perhaps some kind of interaction between Nautilus, Samba and how DHCP servers commonly function. I just can't get a reliable Linux-to-Linux shared network functioning...

I experience this with Ubuntu 10.10 and now with Mint 15 (Ubuntu 13.04) [IMG]http://forums.linuxmint.com/images/smilies/icon_evil.gif[/IMG]

---

### Post by dmizer on 2013-08-01
Have you taken a look here? [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

There is a specific fix related to this error listed under "Problem 5".

---

### Post by CliveMcCarthy on 2013-08-01
Thanks for replying, but I don't have a "Windows" browsing problem. I have a Linux-to-Linux browsing problem. Or, perhaps to put it another way, I have a Samba browsing problem?

Currently I'm sitting at a desk with _three_ Linux machines all _wired_ into a router. When I use the Nautilus view of the network all I see is my wife's Mac and the "Windows Network" -- nothing else. Normally I would see the three Linux machines as well and be able to navigate to their shared directories.

If I run **nbtscan **I can see everything that is active on the network. If I run **smbtree** I can see everything too. Here's the output from **smbtree**&#8203;.

```
KIBBUTZCLIVEWORKGROUP
    \\VOSTROV13              VostroV13 server (Samba, LinuxMint)
        \\VOSTROV13\HP-LaserJet-1200    HP LaserJet 1200
        \\VOSTROV13\HL2270DW           HL2270DW
        \\VOSTROV13\print$             Printer Drivers
        \\VOSTROV13\shareddocs         
        \\VOSTROV13\music              
        \\VOSTROV13\IPC$               IPC Service (VostroV13 server (Samba, LinuxMint))
    \\Q9550                  Q9550 server (Samba, Ubuntu)
        \\Q9550\q9550shareddocs    
        \\Q9550\HL2270DW           HL2270DW
        \\Q9550\HP-LaserJet-4L     HP LaserJet 4L
        \\Q9550\Tricias-HP-LaserJet-1200    Hewlett-Packard HP LaserJet 1200
        \\Q9550\print$             Printer Drivers
        \\Q9550\IPC$               IPC Service (Q9550 server (Samba, Ubuntu))
    \\NETFLIX_HD             Zotac Ion
        \\NETFLIX_HD\SharedDocs         
        \\NETFLIX_HD\IPC$               Remote IPC
    \\MACBOOKPRO-AB2A        Tricia Bell's MacBook Pro
    \\G750                   G750 server (Samba, LinuxMint)
        \\G750\HP_LaserJet_Professional_P1102w    HP LaserJet Professional P1102w @ Tricia Bell’s MacBook Pro
        \\G750\HP_LaserJet_1200    HP LaserJet 1200 @ Tricia Bell’s MacBook Pro
        \\G750\print$             Printer Drivers
        \\G750\shareddocs         G750
        \\G750\IPC$               IPC Service (G750 server (Samba, LinuxMint))
    \\ARTSHOW24              artshow24 server (Samba, Ubuntu)
        \\ARTSHOW24\shareddocs         artshow15 shared
        \\ARTSHOW24\print$             Printer Drivers
        \\ARTSHOW24\IPC$               IPC Service (artshow24 server (Samba, Ubuntu))
    \\ARTSHOW21              artshow21 server (Samba, Ubuntu)
        \\ARTSHOW21\shareddocs         artshow15 shared
        \\ARTSHOW21\print$             Printer Drivers
        \\ARTSHOW21\IPC$               IPC Service (artshow21 server (Samba, Ubuntu))
    \\ARTDEMO                artdemo server (Samba, Ubuntu)
        \\ARTDEMO\shareddocs         
        \\ARTDEMO\C                  development on artdemo
        \\ARTDEMO\music              
        \\ARTDEMO\print$             Printer Drivers
        \\ARTDEMO\IPC$               IPC Service (artdemo server (Samba, Ubuntu))
```

---

### Post by CliveMcCarthy on 2013-08-02
And so, 24 hours later, this Ubuntu machine still is unable to see other shares on other Linux machines. I did reboot the two other Linux machines on my desk and they now can see one another's shares. This machine remains blind. There is something fundamentally wrong with the Nautilus-Samba interface. It somehow caches a view of the network that it NEVER refreshes. **Smbtree** and **Nbtscan** can see the entire network on this machine but Nautilus remains ignorant?

However, somehow the lone Mac on the network shows up! Windows machines -- no, Linux machines -- no. What weird thing is Apple (Darwin) doing that it is more compatible with Ubuntu than Ubuntu is with itself?

---

### Post by Morbius1 on 2013-08-02
I can reproduce some of your symptoms quite easily.

[1] Apple uses 2 mechanisms to announce the availability of a samba share and one of them is zeroconf. Linux also speaks zeroconf and since this is outside the normal samba nmbd process it will display the zerconf enabled service outside of the "Windows Network" folder.

[2] The reason "Windows Network" is empty is because of this:
> KIBBUTZCLIVEWORKGROUP
Has to be 15 characters or less in length and yours is 21. I replaced my workgroup name with yours and can reproduce your error. If I change it to something like this everything returns to normal:
```
KIBBUTZCLIVEWRK
```

So edit /etc/samba/smb.conf and change your workgroup name to something 15 characters or less in length. While you're in there add another line right under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```
Then restart the samba services:
```
sudo service smbd restart
sudo service nmbd restart
```
Do that to all your Linux machines and then go make yourself a nice pot of tea. When you restart nmbd the network has a hissy fit and you need to give it a few minutes to calm itself.

---

### Post by CliveMcCarthy on 2013-08-02
Morbius, thank you for your response. I shall follow your advice.

I have in the past attempted to modify the name resolve order but the network still seem to exhibit problems. Perhaps you can explain, or direct me to a source of information, about how names are resolved? In general, I think order dependent things are to be avoided -- with** bcast, host, lmhosts** and** wins** there are 24 ways of setting the configuration and maybe only one that is correct. Since **smbtree **and **nbtscan** can figure things out for themselves why can't Nautilus? Can't Nautilus try them all, as I presume **nbtscan** does? Clearly the Apple **Bonjour/zeroconf**, that you mentioned, is the most robust method since these shares _always_ show up.

What is troubling is that the network seems to operate satisfactorily for weeks at a time (even with an apparently discrepant name resolution order) and then, spontaneously, each Linux machine then seems to become trapped unable to see anything on the network (except for the Apple Mac) even if rebooted.

My machines all seem to be back with the ability to see each other's shares. Perhaps I should do an experiment and try all 24 orderings of the name resolution list, but since I know the network can work satisfactorily for weeks with a 'wrong' order, I won't be able prove anything conclusively. I've had this problem for several years and I'd like to get it nailed.

What exactly is the mechanism? Does Nautilus/Samba broadcast to the network and make a 'who is out there?' kind of request and get back a list of names and ip addresses? Or does Nautilus/Samba simply communicate with the DHCP server and request the server's list of names and addresses?

I'm also perplexed that I have seen posts suggesting edits to ordering of things in** /etc/nsswitch.conf** as well as **/etc/samba/smb.conf**

Mine reads:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4
```

How do the settings in nsswitch.conf and smb.conf interact? Can things get screwy if these is some way conflict?


[HR][/HR]
I took a fresh look at the workgroup name and it seems I posted the output of **smbtree** incorrectly. There are in fact two workgroups, but they have names shorter than 15 chars.

```

KIBBUTZ
CLIVEWORKGROUP
    \\VOSTROV13              VostroV13 server (Samba, LinuxMint)
        \\VOSTROV13\HP-LaserJet-1200    HP LaserJet 1200
        \\VOSTROV13\HL2270DW           HL2270DW
        \\VOSTROV13\print$             Printer Drivers
        \\VOSTROV13\shareddocs         
        \\VOSTROV13\music              
        \\VOSTROV13\IPC$               IPC Service (VostroV13 server (Samba, LinuxMint))
    \\Q9550                  Q9550 server (Samba, Ubuntu)
        \\Q9550\q9550shareddocs    
        \\Q9550\HL2270DW           HL2270DW
        \\Q9550\HP-LaserJet-4L     HP LaserJet 4L
        \\Q9550\Tricias-HP-LaserJet-1200    Hewlett-Packard HP LaserJet 1200
        \\Q9550\print$             Printer Drivers
        \\Q9550\IPC$               IPC Service (Q9550 server (Samba, Ubuntu))
    \\NETFLIX_HD             Zotac Ion
        \\NETFLIX_HD\SharedDocs         
        \\NETFLIX_HD\IPC$               Remote IPC
    \\MACBOOKPRO-AB2A        Tricia Bell's MacBook Pro
    \\G750                   G750 server (Samba, LinuxMint)
        \\G750\HP_LaserJet_Professional_P1102w    HP LaserJet Professional P1102w @ Tricia Bell’s MacBook Pro
        \\G750\HP_LaserJet_1200    HP LaserJet 1200 @ Tricia Bell’s MacBook Pro
        \\G750\print$             Printer Drivers
        \\G750\shareddocs         G750
        \\G750\IPC$               IPC Service (G750 server (Samba, LinuxMint))

...


```

It looks like a newline screw-up when I pasted the output.

---

### Post by Morbius1 on 2013-08-02
** Don't obsess with all the available permutations of "name resolve order" since host, lmhosts, and wins are non functional by default leaving bcast or broadcast ( same as in Windows ) as the only one that works. And they way you described how bcast works is essentially correct. 

** The Apple way is superior - at least for home networks - primarily because it doesn't depend on nmbd, workgroups, and netbios names to function. Since Linux can speak the language you can always do the poor man's apple. For example:
```
nautilus smb://VOSTROV13.local
```
Then bookmark it. Just remember that zerconf relies on the hostname not the netbios name. Samba forces the netbios to match the host but you may have overridden it smb.conf.

You can also create an avahi samba services file to mimic what OSX does.

*** And yes what you did to nsswitch is not they recommended way to do this sort of thing.

---

### Post by CliveMcCarthy on 2013-08-02
OK, I won't obsess about the ordering complexity, but if **host**, **lmhosts**, and **wins** are non-functional why shouldn't I just trash them and rely on **bcast**? 

The Mac is clearly capable of getting on with things. The odd Windows XP machines might have difficulty perhaps? 

There is something unstable in my network, at least as far as the Linux machines go, so purging redundant or non-functional name resolution schemes might help -- or at least narrow the diagnostic path. What you have explained is very helpful. I can presume that bcast is a zero-configuration protocol. I've been reading Wikipedia:
 [HTML]http://en.wikipedia.org/wiki/Zero_configuration_networking[/HTML]
so my DHCP server isn't likely at fault since it is hardly needed?

By default the **name resolution order** in **smb.conf** is commented out -- is this because **bcast** is the default? In which case there is something periodically going wrong with **bcast** because un-commenting the line was supposed to be a fix for the original problem.

My understanding now is that Nautilus retrieves data from Samba which in turn uses the **bcast** mechanism as a means of locating ip addresses for hostnames?

How should I set nsswitch if "*hosts: files mdns4_minimal [NOTFOUND=return] dns wins mdns4*" is incorrect?

Sorry if it seems I just won't let go of the issue, but this problem has dogged me for several years, and every time I work on it the problem 'goes away' only to resurface sometimes months later...

---

### Post by Morbius1 on 2013-08-02
That's a lot of questions. Let's see how far I can get  :)
>                           OK, I won't obsess about the ordering complexity, but if **host**, **lmhosts**, and **wins** are non-functional why shouldn't I just trash them and rely on **bcast**? 
Some people do just that. Member [COLOR=#0000cd]**bab1**[/COLOR] for example always recommends setting it to just bcast alone. I like to keep my options open so I keep them in. If everything was working perfectly it wouldn't matter what order they were in. Samba would go through each one in turn and find the one that works. Sometimes because of the choice of router or even the ISP they use things get gummed up. 
>  The Mac is clearly capable of getting on with things. The odd Windows XP machines might have difficulty perhaps? 
Windows can join the party with a partial implementation of bonjour - partial in the sense that they too can then connect to other machines with a \\hostname.local. But something has to be installed on Windows to make it work.
> What you have explained is very helpful. I can presume that bcast is a zero-configuration protocol.
bcast is the linux implementation of a native Windows "node" mechanism called broadcast. Avahi is the zeroconf implementation and is contolled by the avahi-daemon service.
> By default the **name resolution order** in **smb.conf** is commented out -- is this because **bcast** is the default?
You know, every single thing about Samba is unnecessarily complex and what you are referring to even messes up seasoned users of it. The ";" in front of the line is one recommendation and one used most often in a corporate setting. The default lists all four and has bcast last. In a corporate setting you want bcast last - you don't want 150 clients to broadcast their presence of the network.

The default nsswitch is this:
> hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
You will note that the mdns references relate to avahi/bonjour/zeroconf and is what makes *.local possible.

---

### Post by CliveMcCarthy on 2013-08-02
Excellent!

I'll put** bcast** first, restore **nsswitch.conf** to the default values on my main machines, and keep my fingers crossed. If things foul-up in the future I'll try restarting** smbd** &** nmbd **as my first line of attack.
Thank you for your patience and your understanding particularly:

[COLOR=#000000]"You know, every single thing about Samba is unnecessarily complex..."

I have to agree [/COLOR]:)

---

### Post by Morbius1 on 2013-08-02
When you have absolutely nothing else to do you might want to explore the miracle of avahi.

**Take one of your Linux machines and create a file:
```
gksu gedit /etc/avahi/services/samba.service
```
** Add this content:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name replace-wildcards="yes">Samba %h</name> ## Display Name
<service>
<type>_smb._tcp</type>
<port>445</port>
</service>
</service-group>

```
[COLOR=#0000cd]*Make sure there are no spaces in front of that first line in the file.*[/COLOR]

**Restart avahi:
```
sudo service avahi-daemon restart
```
Two things should happen:

[1] The mac should automatically ( well... after a second or two ) list "Samba some-host-name" under Network on the left side panel in Finder.
[2] The other Linux boxes should show "Samba some-host-name" when Browse Network is selected - and it should show up in the same place the Mac does - outside of the "Windows Network" folder.

---

### Post by bab1 on 2013-08-02
> **Morbius1 said:**
> That's a lot of questions. Let's see how far I can get  :)

Some people do just that. Member [COLOR=#0000cd]**bab1**[/COLOR] for example always recommends setting it to just bcast alone. I like to keep my options open so I keep them in. If everything was working perfectly it wouldn't matter what order they were in. Samba would go through each one in turn and find the one that works. Sometimes because of the choice of router or even the ISP they use things get gummed up.

I see I have been mentioned.  :)  The reason for the use of only bcast is simple.  Since smbd (Samba) checks each resolve method in the order configured and bcast never fails (unless the whole config is mucked up) there is no reason to add the others.  In fact the only two needed are hosts and bcast.  

Hosts does work if you map the hostname to the IP address in the /etc/hosts file.  This means that you must use static IP addresses to use the *hosts *option (no DHCP).  LMhosts is deprecated (but configurable if you wish to do so) and there is no need for WINS in a single segment Samba setup.

If you want to see smbd go through these steps try this```
smbtree -d3
```...the requests are clearly shown.  It usually ends with bcast finding the Master Browse which *[COLOR="#0000FF"]"retrieve[s the] share list from server[/COLOR]*.  Look for this```
Attempting broadcast lookup for name __MSBROWSE__<0x1>
```

>  

Windows can join the party with a partial implementation of bonjour - partial in the sense that they too can then connect to other machines with a \\hostname.local. But something has to be installed on Windows to make it work.

bcast is the linux implementation of a native Windows "node" mechanism called broadcast. Avahi is the zeroconf implementation and is contolled by the avahi-daemon service.
Bcast referred to here is a Samba thing.  :) > 

You know, every single thing about Samba is unnecessarily complex and what you are referring to even messes up seasoned users of it. The ";" in front of the line is one recommendation and one used most often in a corporate setting. The default lists all four and has bcast last. In a corporate setting you want bcast last - you don't want 150 clients to broadcast their presence of the network.

The default nsswitch is this:

You will note that the mdns references relate to avahi/bonjour/zeroconf and is what makes *.local possible.
I wouldn't mess with the nsswitch.conf file unless you completely understand what you are doing.  The default config is perfectly fine for the average user.

@ Morbius1, Glad to see you are back after our forced 1 week vacation.  LOL

---

### Post by bab1 on 2013-08-02
> **CliveMcCarthy said:**
> OK, I won't obsess about the ordering complexity, but if **host**, **lmhosts**, and **wins** are non-functional why shouldn't I just trash them and rely on **bcast**? 

In my opinion you only need bcast.  See my previous post.  But if you leave the others in it will do no harm.  The order is important.  If you use bcast first, you don't need to wory about Samba hanging up on the others. > 

The Mac is clearly capable of getting on with things. The odd Windows XP machines might have difficulty perhaps? 

There is something unstable in my network, at least as far as the Linux machines go, so purging redundant or non-functional name resolution schemes might help -- or at least narrow the diagnostic path. What you have explained is very helpful. I can presume that bcast is a zero-configuration protocol. I've been reading Wikipedia:
 [HTML]http://en.wikipedia.org/wiki/Zero_configuration_networking[/HTML]
so my DHCP server isn't likely at fault since it is hardly needed?
AVAHI is a suite of tools.  The zeroconf part works in the absence of a DHCP server.  It provides an IP address in the 169.254.0.0 /16 network and is link local (LAN only).  The mDNS is part is the local only DNS which you see as .local.  This can work along side of other naming schemes.  In fact I can call my Samba server with either //SERVER or //SERVER.local. > 

By default the **name resolution order** in **smb.conf** is commented out -- is this because **bcast** is the default? In which case there is something periodically going wrong with **bcast** because un-commenting the line was supposed to be a fix for the original problem.

The default is exactly what is "commented out".  It is used whether you just uncomment it or not.  The reason for uncommenting is to let you remove types or change the order (ie change the defaults).
> 

My understanding now is that Nautilus retrieves data from Samba which in turn uses the **bcast** mechanism as a means of locating ip addresses for hostnames?

Samba uses the broadcasts to build the "share list" at the Master Browser.  Samba delivers the information when Nautilus requests to mount the share so it can browse it. 
> 

How should I set nsswitch if "*hosts: files mdns4_minimal [NOTFOUND=return] dns wins mdns4*" is incorrect?

Leave it at the default settings.
> 

Sorry if it seems I just won't let go of the issue, but this problem has dogged me for several years, and every time I work on it the problem 'goes away' only to resurface sometimes months later...
It is helpful to understand that Samba is also suite of tools.  Browing is just one part of it.  It relies heavily on either accessing the hostname to IP address mapping (hosts/DNS) to convert this to NETBIOS names or directly by using an explicitly configured NETBIOS name in the smb.conf file.

[COLOR="#0000FF"]Edit:  This is really a high level view of Samba.  It really doesn't directly address HOW to fix your problems.  I have strong feelings regarding folks stepping on others work as they are helping you.  @Morbius1 is very good Samba diagnosis.  I would follow what he has to offer. [/COLOR]

---

### Post by Morbius1 on 2013-08-02
@bab1, even if I didn't mention you by name  I figured you were looking in anyway - I know you can't resist samba questions  :p

---

### Post by bab1 on 2013-08-02
> **Morbius1 said:**
> @bab1, even if I didn't mention you by name  I figured you were looking in anyway - I know you can't resist samba questions  :p
I try and stay away, but alas, I'm addicted.  :D

---

### Post by CliveMcCarthy on 2013-08-02
I reconfigured two machines as discussed above and [COLOR=#000000]restarted both[/COLOR]** smbd &[B] nmbd**[/B]. I then fired up _nine_ other Linux machines on the network as a kind of stress test. Most of them are running 10.10 but some are running more recent versions of Ubuntu.

The newly added machines don't show up in Nautilus. I hit refresh, nothing new appears. I restart [COLOR=#000000]both[/COLOR]** smbd &[B] nmbd**[/B] again but things remain the same. I rebooted one of the two test machines and voila! the full list of machines appears in Nautilus. I run **smbtree** on the machine that hasn't been rebooted and all the newly added machines show up. So is Nautilus caching things it gets from Samba? What exactly does a Nautilus refresh do, perhaps it just repaints the window? -- that ain't right :rolleyes:

Short of rebooting a machine, how can I force Nautilus-Samba-bcast to re-scan the network?

---

### Post by Morbius1 on 2013-08-02
> By default the **name resolution order** in **smb.conf** is commented out -- is this because **bcast** is the default? In which case there is something periodically going wrong with **bcast** because un-commenting the line was supposed to be a fix for the original problem.                            
[QUOTE]The default is exactly what is "commented out".[/QUOTE]
Don't mean to add confusion but the commented out line is not actually the default as it is with say ... "security = user".

The default is:
> testparm -sv /dev/null | grep "name resolve order"
Load smb config files from /dev/null
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Loaded services file OK.
Server role: ROLE_STANDALONE
    [COLOR=#0000cd]**name resolve order = lmhosts wins host bcast**[/COLOR]

The commented out one on smb.conf is:
> name resolve order = lmhosts host wins bcast
Either way bcast is last and in a home network it should be first - or by itself ;)

---

### Post by bab1 on 2013-08-02
> **Morbius1 said:**
> Don't mean to add confusion but the commented out line is not actually the default as it is with say ... "security = user".

The default is:

The commented out one on smb.conf is:

Either way bcast is last.
I never noticed that they were different.  :(

I always use: hosts: bcast for my servers.

[COLOR="#0000FF"]Edit:  My best guess is that it hangs on WINS looking for the response either way.[/COLOR]

---

### Post by Morbius1 on 2013-08-02
> **CliveMcCarthy said:**
> I reconfigured two machines as discussed above and [COLOR=#000000]restarted both[/COLOR]** smbd &[B] nmbd**[/B]. I then fired up _nine_ other Linux machines on the network as a kind of stress test. Most of them are running 10.10 but some are running more recent versions of Ubuntu.

The newly added machines don't show up in Nautilus. I hit refresh, nothing new appears. I restart [COLOR=#000000]both[/COLOR]** smbd &[B] nmbd**[/B] again but things remain the same. I rebooted one of the two test machines and voila! the full list of machines appears in Nautilus. I run **smbtree** on the machine that hasn't been rebooted and all the newly added machines show up. So is Nautilus caching things it gets from Samba? What exactly does a Nautilus refresh do, perhaps it just repaints the window? -- that ain't right :rolleyes:

Short of rebooting a machine, how can I force Nautilus-Samba-bcast to re-scan the network?
What about the only two that you reconfigured. Do they see each other? And when you say reconfigured are we talking about avahi or the name resolve order thing? There is always a disruption when new machines are added to the network if you use the standard Samba process - Even between Windows. You need to give it a few moments.

---

### Post by CliveMcCarthy on 2013-08-02
By reconfigured I mean I set** bcast** first, and reset **nsswitch** to the default setting removing the "wins".

The two test machines can still see each other and each other's shares. The rebooted machine can see _all_ the machines I added to the network but the un-rebooted machine can't. It's as if Nautilus took a snapshot of what Samba once scanned, cached the results, and now refuses to ask Samba again...

I'm glad you guys sorted out the default behavior in this thread, it might have been confusing to others...

Supplemental: If I look inside the** Windows Network** all the added machines can be seen!

---

### Post by bab1 on 2013-08-02
> **Morbius1 said:**
> What about the only two that you reconfigured. Do they see each other? And when you say reconfigured are we talking about avahi or the name resolve order thing? There is always a disruption when new machines are added to the network if you use the standard Samba process - Even between Windows. You need to give it a few moments.
+ 1 for that.

If I may.  The rescan is not what you think it is.  The Master Browser (MB) is elected amongst the running machines.  If you turn off the computer that hosts the MB then the election can take some time while the browse list is remade.  The tool smbtree uses a different method to method to create the tree that you see at the command line.  Nautilus caches nothing, it is only browsing the shares that are mounted.  In fact browsing causes share to be mounted if they are not already mounted.

---

### Post by Morbius1 on 2013-08-02
Well, if you only changed the bcast and nsswitch on 2 then the others are still using the old settings. 

I don't think rebooting is the key here but keep hitting the Reload button on Nautilus ( view > Reload ).

The standard way of doing this in Samba even with the settings changes will always be slower than avahi - especially since you threw 9 machines into the mix. - [COLOR=#0000cd]EDIT[/COLOR] - for the reason bab1 just posted.

---

### Post by bab1 on 2013-08-02
> **Morbius1 said:**
> Well, if you only changed the bcast and nsswitch on 2 then the others are still using the old settings.


I think it's important to note that we are talking about all Samba servers here; not Samba clients (Linux hosts that can browse the SMB/CIFS network).  Clients work correctly by default (unless name services are not working correctly).
> 
I don't think rebooting is the key here but keep hitting the Reload button on Nautilus ( view > Reload )....

---

### Post by bab1 on 2013-08-02
> Supplemental: If I look inside the Windows Network all the added machines can be seen! 
As it should be.  The Windows Network includes all SMB/CIFS servers and shares.  When you see them outside of that it is just for your convenience.  That ***[COLOR="#0000FF"]view[/COLOR]*** is a Nautilus thing.

---

### Post by Morbius1 on 2013-08-02
Look fellas, I should have shut down 2 hours ago so if bab1 wants to continue with this I have no problem with that. We rarely disagree on many things these days. 

If not I'll be back at it tomorrow - although my wife is the master of my weekends so I don't know when tomorrow.

---

### Post by CliveMcCarthy on 2013-08-02
It's over an hour later than my last post and the un-rebooted machine's Nautilus still doesn't show the machines I added to the network. **Smbtree** sees them just fine, when I run it. For my next experiment I might try terminating Nautilus which I gather from my past reading, will be automatically re-instated. This seems a rather brutal approach.

---

### Post by bab1 on 2013-08-02
Before you do that please post the output of```
smbtree -d3
```

I want to see what is going on behind the scenes.

On one of those hosts you are referring to try this```
smbclient -d3 -L <Server>
```...where <Server> is the other un-seen machine.

---

### Post by CliveMcCarthy on 2013-08-02
Morbius, thanks for all your help -- it is just late afternoon here in San Francisco...

I hit **view > reload** and it does nothing new.

I think I can figure out which machine has been elected the Master Browser from the output of **smbtree -d3** I see that part of the response is:
```
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.2.33 ( 192.168.2.35 )
```
I have looked up the ip address and it is a machine that has been running for weeks and weeks (it is just a music server). I've just checked what it thinks the network looks like and it sees ALL the machines.

So what remains a puzzle is why the machine I'm investigating hasn't refreshed itself from the designated __MSBROWSE__ machine. The __MSBROWSE__ machine is visible from Nautilus on the machine I'm investigating.

If Nautilus isn't caching anything where is it looking when I ask for a refresh? Could things be fouled up because the __MSBROWSE__ machine has two valid ip addresses? It so happens it is connected both wired and wirelessly and so has two ip addresses.

---

### Post by CliveMcCarthy on 2013-08-02
Here is the output from **smbtree -d3** from the 'blind' machine.
```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::224:d6ff:fe21:8f28%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=fe80::226:6cff:fe10:105f%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.2.24 bcast=192.168.2.255 netmask=255.255.255.0
added interface eth0 ip=192.168.2.40 bcast=192.168.2.255 netmask=255.255.255.0
Enter clive's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name CLIVEWORKGROUP<0x1d>
Got a positive name query response from 192.168.2.33 ( 192.168.2.35 )
Connecting to host=192.168.2.35
Connecting to 192.168.2.35 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.2.33 ( 192.168.2.35 )
name_resolve_bcast: Attempting broadcast lookup for name CLIVEWORKGROUP<0x1d>
Got a positive name query response from 192.168.2.33 ( 192.168.2.35 )
Connecting to host=192.168.2.35
Connecting to 192.168.2.35 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
CLIVEWORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name CLIVEWORKGROUP<0x1d>
Got a positive name query response from 192.168.2.33 ( 192.168.2.35 )
Connecting to host=192.168.2.35
Connecting to 192.168.2.35 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\VOSTROV13              VostroV13 server (Samba, LinuxMint)
Connecting to host=VOSTROV13
name_resolve_bcast: Attempting broadcast lookup for name VOSTROV13<0x20>
Got a positive name query response from 192.168.2.40 ( 192.168.2.40 )
Connecting to 192.168.2.40 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\VOSTROV13\HP-LaserJet-1200    HP LaserJet 1200
        \\VOSTROV13\HL2270DW           HL2270DW
        \\VOSTROV13\IPC$               IPC Service (VostroV13 server (Samba, LinuxMint))
        \\VOSTROV13\music              
        \\VOSTROV13\shareddocs         
        \\VOSTROV13\print$             Printer Drivers
    \\Q9550                  Q9550 server (Samba, LinuxMint)
Connecting to host=Q9550
name_resolve_bcast: Attempting broadcast lookup for name Q9550<0x20>
Got a positive name query response from 192.168.2.28 ( 192.168.2.28 )
Connecting to 192.168.2.28 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\Q9550\Brother-HL-2270DW-series    Brother HL-2270DW series
        \\Q9550\print$             Printer Drivers
        \\Q9550\shareddocs         q9550
        \\Q9550\IPC$               IPC Service (Q9550 server (Samba, LinuxMint))
    \\OPUS38                 opus38 server (Samba, LinuxMint)
Connecting to host=OPUS38
name_resolve_bcast: Attempting broadcast lookup for name OPUS38<0x20>
Got a positive name query response from 192.168.2.25 ( 192.168.2.25 )
Connecting to 192.168.2.25 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\OPUS38\print$             Printer Drivers
        \\OPUS38\shareddocs         
        \\OPUS38\IPC$               IPC Service (opus38 server (Samba, LinuxMint))
    \\NETFLIX_HD             Zotac Ion
Connecting to host=NETFLIX_HD
name_resolve_bcast: Attempting broadcast lookup for name NETFLIX_HD<0x20>
Got a positive name query response from 192.168.2.11 ( 192.168.2.11 )
Connecting to 192.168.2.11 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\NETFLIX_HD\SharedDocs         
        \\NETFLIX_HD\IPC$               Remote IPC
    \\MACBOOKPRO-AB2A        Tricia Bell's MacBook Pro
Connecting to host=MACBOOKPRO-AB2A
name_resolve_bcast: Attempting broadcast lookup for name MACBOOKPRO-AB2A<0x20>
Got a positive name query response from 192.168.2.30 ( 192.168.2.30 )
Connecting to 192.168.2.30 at port 445
Doing spnego session setup (blob length=144)
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.752.43.14.3
got OID=1.3.6.1.5.5.14
got OID=1.3.6.1.4.1.311.2.2.10
got OID=1.3.5.1.5.2.7
got OID=1.3.6.1.5.2.5
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x60898235
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
anonymous failed session setup with NT_STATUS_PIPE_BROKEN
    \\INSPIRON8000           
Connecting to host=INSPIRON8000
name_resolve_bcast: Attempting broadcast lookup for name INSPIRON8000<0x20>
Got a positive name query response from 192.168.2.19 ( 192.168.2.19 )
Connecting to 192.168.2.19 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\INSPIRON8000\Printer            Microsoft XPS Document Writer
        \\INSPIRON8000\HPLaserJet 1200    HP LaserJet 1200 Series PCL
        \\INSPIRON8000\print$             Printer Drivers
        \\INSPIRON8000\SharedDocs         
        \\INSPIRON8000\IPC$               Remote IPC
        \\INSPIRON8000\HPLaserJet4L       HP LaserJet 4L
    \\ARTSHOW45              artshow45 server (Samba, Ubuntu)
Connecting to host=ARTSHOW45
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW45<0x20>
Got a positive name query response from 192.168.2.18 ( 192.168.2.49 )
Connecting to 192.168.2.49 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW45\shareddocs         artshow15 shared
        \\ARTSHOW45\IPC$               IPC Service (artshow45 server (Samba, Ubuntu))
        \\ARTSHOW45\print$             Printer Drivers
    \\ARTSHOW44              artshow44 server (Samba, Ubuntu)
Connecting to host=ARTSHOW44
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW44<0x20>
Got a positive name query response from 192.168.2.20 ( 192.168.2.20 )
Connecting to 192.168.2.20 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW44\shareddocs         artshow15 shared
        \\ARTSHOW44\IPC$               IPC Service (artshow44 server (Samba, Ubuntu))
        \\ARTSHOW44\print$             Printer Drivers
    \\ARTSHOW43              artshow43 server (Samba, Ubuntu)
Connecting to host=ARTSHOW43
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW43<0x20>
Got a positive name query response from 192.168.2.32 ( 192.168.2.37 )
Connecting to 192.168.2.37 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW43\shareddocs         artshow15 shared
        \\ARTSHOW43\IPC$               IPC Service (artshow43 server (Samba, Ubuntu))
        \\ARTSHOW43\print$             Printer Drivers
    \\ARTSHOW35              artshow35 server (Samba, Ubuntu)
Connecting to host=ARTSHOW35
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW35<0x20>
Got a positive name query response from 192.168.2.48 ( 192.168.2.48 )
Connecting to 192.168.2.48 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW35\shareddocs         
        \\ARTSHOW35\print$             Printer Drivers
        \\ARTSHOW35\IPC$               IPC Service (artshow35 server (Samba, Ubuntu))
    \\ARTSHOW34              artshow34 server (Samba, Ubuntu)
Connecting to host=ARTSHOW34
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW34<0x20>
Got a positive name query response from 192.168.2.21 ( 192.168.2.21 )
Connecting to 192.168.2.21 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW34\shareddocs         
        \\ARTSHOW34\print$             Printer Drivers
        \\ARTSHOW34\IPC$               IPC Service (artshow34 server (Samba, Ubuntu))
    \\ARTSHOW33              artshow33 server (Samba, Ubuntu)
Connecting to host=ARTSHOW33
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW33<0x20>
Got a positive name query response from 192.168.2.23 ( 192.168.2.23 )
Connecting to 192.168.2.23 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW33\shareddocs         
        \\ARTSHOW33\IPC$               IPC Service (artshow33 server (Samba, Ubuntu))
        \\ARTSHOW33\print$             Printer Drivers
    \\ARTSHOW24              artshow24 server (Samba, Ubuntu)
Connecting to host=ARTSHOW24
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW24<0x20>
Got a positive name query response from 192.168.2.12 ( 192.168.2.12 )
Connecting to 192.168.2.12 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW24\shareddocs         artshow15 shared
        \\ARTSHOW24\print$             Printer Drivers
        \\ARTSHOW24\IPC$               IPC Service (artshow24 server (Samba, Ubuntu))
    \\ARTSHOW21              artshow21 server (Samba, Ubuntu)
Connecting to host=ARTSHOW21
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW21<0x20>
Got a positive name query response from 192.168.2.42 ( 192.168.2.42 )
Connecting to 192.168.2.42 at port 445
Connecting to 192.168.2.42 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW21\shareddocs         artshow15 shared
        \\ARTSHOW21\print$             Printer Drivers
        \\ARTSHOW21\IPC$               IPC Service (artshow21 server (Samba, Ubuntu))
    \\ARTSHOW15              artshow15 server (Samba, Ubuntu)
Connecting to host=ARTSHOW15
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW15<0x20>
Got a positive name query response from 192.168.2.46 ( 192.168.2.46 )
Connecting to 192.168.2.46 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW15\shareddocs         artshow15 shared
        \\ARTSHOW15\print$             Printer Drivers
        \\ARTSHOW15\IPC$               IPC Service (artshow15 server (Samba, Ubuntu))
    \\ARTDEMO                artdemo server (Samba, Ubuntu)
Connecting to host=ARTDEMO
name_resolve_bcast: Attempting broadcast lookup for name ARTDEMO<0x20>
Got a positive name query response from 192.168.2.33 ( 192.168.2.35 )
Connecting to 192.168.2.35 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTDEMO\shareddocs         
        \\ARTDEMO\C                  development on artdemo
        \\ARTDEMO\music              
        \\ARTDEMO\print$             Printer Drivers
        \\ARTDEMO\IPC$               IPC Service (artdemo server (Samba, Ubuntu))

```

---

### Post by bab1 on 2013-08-02
What happens if you do this```
sudo service smbd restart 

sudo service nmbd restart
```...do you see the missing shares?

Are all these servers NETBIOS names defined in the smb.conf file like this```
netbios name = <NETBIOS_NAME>
```...where <NETBIOS_NAME> is what you configure?

[COLOR="#0000FF"]Edit:  What are these 2 IP addresses go to: [/COLOR]**192.168.2.33 ( 192.168.2.35 )**

---

### Post by CliveMcCarthy on 2013-08-02
> **bab1 said:**
> What happens if you do this```
sudo service smbd restart 

sudo service nmbd restart
```...do you see the missing shares?

No, restarting the services does nothing.

> **bab1 said:**
> 
Are all these servers NETBIOS names defined in the smb.conf file like this```
netbios name = <NETBIOS_NAME>
```...where <NETBIOS_NAME> is what you configure?

[COLOR=#0000FF]Edit:  What are these 2 IP addresses go to: [/COLOR]**192.168.2.33 ( 192.168.2.35 )**

I'm not sure I understand what you mean about the NETBIOS names in smb.conf. 

The two ip addresses belong to a machine on the network that appears to be the __MSBROWSE__ machine (see my earlier post).

---

### Post by CliveMcCarthy on 2013-08-02
This is what a Netbios scan looks like:
```
Doing NBT name scan for addresses from 192.168.2.10-50

IP address       NetBIOS Name     Server    User             MAC address      
------------------------------------------------------------------------------
192.168.2.11     NETFLIX_HD       <server>  <unknown>        00:01:2e:33:06:ad
192.168.2.24     VOSTROV13        <server>  VOSTROV13        00:00:00:00:00:00
192.168.2.28     Q9550            <server>  Q9550            00:00:00:00:00:00
192.168.2.18     ARTSHOW45        <server>  ARTSHOW45        00:00:00:00:00:00
192.168.2.25     OPUS38           <server>  OPUS38           00:00:00:00:00:00
192.168.2.21     ARTSHOW34        <server>  ARTSHOW34        00:00:00:00:00:00
192.168.2.40     VOSTROV13        <server>  VOSTROV13        00:00:00:00:00:00
192.168.2.23     ARTSHOW33        <server>  ARTSHOW33        00:00:00:00:00:00
192.168.2.20     ARTSHOW44        <server>  ARTSHOW44        00:00:00:00:00:00
192.168.2.32     ARTSHOW43        <server>  ARTSHOW43        00:00:00:00:00:00
192.168.2.35     ARTDEMO          <server>  ARTDEMO          00:00:00:00:00:00
192.168.2.33     ARTDEMO          <server>  ARTDEMO          00:00:00:00:00:00
192.168.2.37     ARTSHOW43        <server>  ARTSHOW43        00:00:00:00:00:00
192.168.2.48     ARTSHOW35        <server>  ARTSHOW35        00:00:00:00:00:00
192.168.2.49     ARTSHOW45        <server>  ARTSHOW45        00:00:00:00:00:00
192.168.2.12     ARTSHOW24        <server>  ARTSHOW24        00:00:00:00:00:00
192.168.2.46     ARTSHOW15        <server>  ARTSHOW15        00:00:00:00:00:00
192.168.2.30     MACBOOKPRO-AB2A  <server>  <unknown>        60:33:4b:2a:ce:b1
192.168.2.39     BRW0080927F9099  <server>  <unknown>        00:80:92:7f:90:99

```
ARTDEMO appears to be the __MSBROWSE__ machine. VOSTROV13 is the blind machine. Q9550 is the machine I rebooted and it sees everything.

---

### Post by bab1 on 2013-08-02
> **CliveMcCarthy said:**
> No, restarting the services does nothing.


Nothing is returned to the screen?  When I do that for smbd I get this```
smbd stop/waiting
smbd start/running, process 6824

```
Are you sure that Samba is running?  What do you get from this```
ps -ef|grep mbd
```
> 



I'm not sure I understand what you mean about the NETBIOS names in smb.conf.

Samba uses NETBIOS names to map to IP addresses.  This is a NETBIOS name: VOSTROV13.  How do you configure these?
> 

The two ip addresses belong to a machine on the network that appears to be the __MSBROWSE__ machine (see my earlier post).
I can see that.  The machine should have one IP address not two.  So I'll ask it a little differently.  What hosts are these addresses assigned to?

---

### Post by CliveMcCarthy on 2013-08-02
Here's the smb.conf from the 'blind' machine:
```
## Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#


#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = CLIVEWORKGROUP


# server string is the equivalent of the NT Description field
   server string = %h server (Samba, LinuxMint)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = bcast lmhosts wins host
#   name resolve order = bcast host


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).
   max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user


# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam


   obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user


########## Domains ###########


# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g


########## Printing ##########


# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes


# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap


# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY


# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &


# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes


# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom




[shareddocs]
path = /home/clive/Desktop/shareddocs
available = yes
browsable = yes
public = yes
writable = yes


[music]
path = /home/clive/Desktop/music
available = yes
browsable = yes
public = yes
writable = yes
```

---

### Post by bab1 on 2013-08-02
> **CliveMcCarthy said:**
> This is what a Netbios scan looks like:
```
Doing NBT name scan for addresses from 192.168.2.10-50

IP address       NetBIOS Name     Server    User             MAC address      
------------------------------------------------------------------------------
192.168.2.11     NETFLIX_HD       <server>  <unknown>        00:01:2e:33:06:ad
192.168.2.24     VOSTROV13        <server>  VOSTROV13        00:00:00:00:00:00
192.168.2.28     Q9550            <server>  Q9550            00:00:00:00:00:00
192.168.2.18     ARTSHOW45        <server>  ARTSHOW45        00:00:00:00:00:00
192.168.2.25     OPUS38           <server>  OPUS38           00:00:00:00:00:00
192.168.2.21     ARTSHOW34        <server>  ARTSHOW34        00:00:00:00:00:00
192.168.2.40     VOSTROV13        <server>  VOSTROV13        00:00:00:00:00:00
192.168.2.23     ARTSHOW33        <server>  ARTSHOW33        00:00:00:00:00:00
192.168.2.20     ARTSHOW44        <server>  ARTSHOW44        00:00:00:00:00:00
192.168.2.32     ARTSHOW43        <server>  ARTSHOW43        00:00:00:00:00:00
192.168.2.35     ARTDEMO          <server>  ARTDEMO          00:00:00:00:00:00
192.168.2.33     ARTDEMO          <server>  ARTDEMO          00:00:00:00:00:00
192.168.2.37     ARTSHOW43        <server>  ARTSHOW43        00:00:00:00:00:00
192.168.2.48     ARTSHOW35        <server>  ARTSHOW35        00:00:00:00:00:00
192.168.2.49     ARTSHOW45        <server>  ARTSHOW45        00:00:00:00:00:00
192.168.2.12     ARTSHOW24        <server>  ARTSHOW24        00:00:00:00:00:00
192.168.2.46     ARTSHOW15        <server>  ARTSHOW15        00:00:00:00:00:00
192.168.2.30     MACBOOKPRO-AB2A  <server>  <unknown>        60:33:4b:2a:ce:b1
192.168.2.39     BRW0080927F9099  <server>  <unknown>        00:80:92:7f:90:99

```
ARTDEMO appears to be the __MSBROWSE__ machine. VOSTROV13 is the blind machine. Q9550 is the machine I rebooted and it sees everything.

What makes you think that ARTDEMO is the _MSBROWSE_ machine?

This needs to be fixed```

192.168.2.[COLOR="#0000CD"]**35**[/COLOR]     ARTDEMO          <server>  ARTDEMO          00:00:00:00:00:00
192.168.2.[COLOR="#FF0000"]**33**[/COLOR]     ARTDEMO          <server>  ARTDEMO          00:00:00:00:00:00

```...each machine should have only one IP address in the LAN.  Why does this machine have two?

From Q9550, what do you get from this ```
smbclient = artdemo 
```... and this one too```
smbclient -L artshow24
```

---

### Post by CliveMcCarthy on 2013-08-02
When I said "nothing" I meant there was no change to refreshing Nautilus even though I has started and stopped the two services. The services did report that they had stopped/waited/started

---

### Post by bab1 on 2013-08-02
Are you aware that this is **not** being used at this time?
```
**#**   name resolve order = bcast host
```...you have to remove the hash tag **(#)** for it to be used as a smb.conf parameter.

---

### Post by CliveMcCarthy on 2013-08-02
ARTDEMO has two ip addresses because it is connected both wirelessly and is wired -- it does that.

---

### Post by bab1 on 2013-08-02
How about the other questions I have asked?

---

### Post by CliveMcCarthy on 2013-08-02
both show that ARTDEMO is the master for the CLIVEWORKGROUP

---

### Post by CliveMcCarthy on 2013-08-02
yes, I understand that #'s comment out lines in smb.conf

---

### Post by CliveMcCarthy on 2013-08-02
From the 'blind' machine:

```
Domain=[CLIVEWORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (artdemo server (Samba, Ubuntu))
    print$          Disk      Printer Drivers
    music           Disk      
    C               Disk      development on artdemo
    shareddocs      Disk      
Domain=[CLIVEWORKGROUP] OS=[Unix] Server=[Samba 3.6.3]


    Server               Comment
    ---------            -------
    ARTDEMO              artdemo server (Samba, Ubuntu)
    ARTSHOW15            artshow15 server (Samba, Ubuntu)
    ARTSHOW21            artshow21 server (Samba, Ubuntu)
    ARTSHOW24            artshow24 server (Samba, Ubuntu)
    ARTSHOW33            artshow33 server (Samba, Ubuntu)
    ARTSHOW34            artshow34 server (Samba, Ubuntu)
    ARTSHOW35            artshow35 server (Samba, Ubuntu)
    ARTSHOW43            artshow43 server (Samba, Ubuntu)
    ARTSHOW44            artshow44 server (Samba, Ubuntu)
    ARTSHOW45            artshow45 server (Samba, Ubuntu)
    MACBOOKPRO-AB2A      Tricia Bell's MacBook Pro
    NETFLIX_HD           Zotac Ion
    OPUS38               opus38 server (Samba, LinuxMint)
    Q9550                Q9550 server (Samba, LinuxMint)
    VOSTROV13            VostroV13 server (Samba, LinuxMint)


    Workgroup            Master
    ---------            -------
    CLIVEWORKGROUP       ARTDEMO



```

So it is evident that all machines know that ARTDEMO is the master -- 'blind' and 'seeing'.

---

### Post by bab1 on 2013-08-02
From ARTDEMO post the output of ```
ifconfig
```...don't tell me what it says, show me the output.

---

### Post by CliveMcCarthy on 2013-08-02
Here are the smbclient -L responses from Q9550 about ARTDEMO and ARTSHOW24

```
clive@Q9550 ~ $ smbclient  -L artdemo
Enter clive's password: 
Domain=[CLIVEWORKGROUP] OS=[Unix] Server=[Samba 3.6.3]


    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (artdemo server (Samba, Ubuntu))
    print$          Disk      Printer Drivers
    music           Disk      
    C               Disk      development on artdemo
    shareddocs      Disk      
Domain=[CLIVEWORKGROUP] OS=[Unix] Server=[Samba 3.6.3]


    Server               Comment
    ---------            -------
    ARTDEMO              artdemo server (Samba, Ubuntu)
    ARTSHOW15            artshow15 server (Samba, Ubuntu)
    ARTSHOW21            artshow21 server (Samba, Ubuntu)
    ARTSHOW24            artshow24 server (Samba, Ubuntu)
    ARTSHOW33            artshow33 server (Samba, Ubuntu)
    ARTSHOW34            artshow34 server (Samba, Ubuntu)
    ARTSHOW35            artshow35 server (Samba, Ubuntu)
    ARTSHOW43            artshow43 server (Samba, Ubuntu)
    ARTSHOW44            artshow44 server (Samba, Ubuntu)
    ARTSHOW45            artshow45 server (Samba, Ubuntu)
    MACBOOKPRO-AB2A      Tricia Bell's MacBook Pro
    NETFLIX_HD           Zotac Ion
    OPUS38               opus38 server (Samba, LinuxMint)
    Q9550                Q9550 server (Samba, LinuxMint)
    VOSTROV13            VostroV13 server (Samba, LinuxMint)


    Workgroup            Master
    ---------            -------
    CLIVEWORKGROUP       ARTDEMO
clive@Q9550 ~ $ smbclient  -L artshow24
Enter clive's password: 
Domain=[CLIVEWORKGROUP] OS=[Unix] Server=[Samba 3.5.4]


    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (artshow24 server (Samba, Ubuntu))
    print$          Disk      Printer Drivers
    shareddocs      Disk      artshow15 shared
Domain=[CLIVEWORKGROUP] OS=[Unix] Server=[Samba 3.5.4]


    Server               Comment
    ---------            -------
    ARTDEMO              artdemo server (Samba, Ubuntu)
    ARTSHOW24            artshow24 server (Samba, Ubuntu)


    Workgroup            Master
    ---------            -------
    CLIVEWORKGROUP       ARTDEMO
clive@Q9550 ~ $ 



```

---

### Post by CliveMcCarthy on 2013-08-02
from VOSTROV13 the 'blind' machine:
```
  
clive@VostroV13 ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:6c:10:10:5f  
          inet addr:192.168.2.40  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe10:105f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147821 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67350985 (67.3 MB)  TX bytes:28135408 (28.1 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:878486 (878.4 KB)  TX bytes:878486 (878.4 KB)


wlan0     Link encap:Ethernet  HWaddr 00:24:d6:21:8f:28  
          inet addr:192.168.2.24  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d6ff:fe21:8f28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8460654 (8.4 MB)  TX bytes:76297 (76.2 KB)


clive@VostroV13 ~ $ 



```

---

### Post by bab1 on 2013-08-02
> If Nautilus isn't caching anything where is it looking when I ask for a refresh? Could things be fouled up because the __MSBROWSE__ machine has two valid ip addresses? It so happens it is connected both wired and wirelessly and so has two ip addresses. 
I must have missed this post when we had a number of them at the same time.  This can cause problems.  I'm wondering if both IP addresses are active at the same time. 

At this point the *ifconfig *command is all we need right now.  If both are active, down the wireless connection and restart smbd and nmbd.  There is no need to rehoot the machine as rebooting just causes smbd and nmbd to reread the smb.conf file as does restarting the 2 daemons.

---

### Post by bab1 on 2013-08-02
> **CliveMcCarthy said:**
> from VOSTROV13 the 'blind' machine:
```
  
clive@VostroV13 ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:6c:10:10:5f  
          inet addr:192.168.2.40  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe10:105f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147821 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67350985 (67.3 MB)  TX bytes:28135408 (28.1 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:878486 (878.4 KB)  TX bytes:878486 (878.4 KB)


wlan0     Link encap:Ethernet  HWaddr 00:24:d6:21:8f:28  
          inet addr:192.168.2.24  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d6ff:fe21:8f28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8460654 (8.4 MB)  TX bytes:76297 (76.2 KB)


clive@VostroV13 ~ $ 



```

I'm interested in ifconfig from ARTDEMO not VostroV13

---

### Post by CliveMcCarthy on 2013-08-02
Would you like the ifconfig data from the __MSBROWSER__ ARTDEMO master? Should I unplug the wired connection to it so that only has one ip address? It seems that can't be the problem because Q9550 became OK (went from blind to seeing) after it was rebooted but ARTDEMO still had/has two ip addresses.

---

### Post by CliveMcCarthy on 2013-08-02
```

clive@artdemo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:6c:f4:aa  
          inet addr:192.168.2.33  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::8aae:1dff:fe6c:f4aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:419733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93821 errors:14 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71170659 (71.1 MB)  TX bytes:10191671 (10.1 MB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:149212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11659529 (11.6 MB)  TX bytes:11659529 (11.6 MB)


wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:89:68:0a  
          inet addr:192.168.2.35  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:fe89:680a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1411246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:265028659 (265.0 MB)  TX bytes:39865690 (39.8 MB)


clive@artdemo:~$ 



```

---

### Post by bab1 on 2013-08-02
> **CliveMcCarthy said:**
> Would you like the ifconfig data from the __MSBROWSER__ ARTDEMO master? Should I unplug the wired connection to it so that only has one ip address? It seems that can't be the problem because Q9550 became OK (went from blind to seeing) after it was rebooted but ARTDEMO still had/has two ip addresses.

I can't see the entire topology of your network so I am making some assumptions here.  i want you to show me the output of the *IFCONFIG *command on ARTDEMO.

In theory you should have only one IP address per host in the same subnet.  This means that ARTDEMO should have one of the interfaces disabled by the protocol STP.  I want to star there with diagnosis.

---

### Post by bab1 on 2013-08-02
> **CliveMcCarthy said:**
> ```

clive@artdemo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:6c:f4:aa  
          inet addr:192.168.2.33  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::8aae:1dff:fe6c:f4aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:419733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93821 errors:14 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71170659 (71.1 MB)  TX bytes:10191671 (10.1 MB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:149212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11659529 (11.6 MB)  TX bytes:11659529 (11.6 MB)


wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:89:68:0a  
          inet addr:192.168.2.35  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:fe89:680a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1411246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:265028659 (265.0 MB)  TX bytes:39865690 (39.8 MB)


clive@artdemo:~$ 



```

Do you have a wireless router (a router that serves your wireless hosts)?

---

### Post by CliveMcCarthy on 2013-08-02
Bab1,
I have to take a break to start cooking dinner. Thanks for your patience on this matter. I shall return when the household is fed!
Clive.

---

### Post by bab1 on 2013-08-02
> **CliveMcCarthy said:**
> Bab1,
I have to take a break to start cooking dinner. Thanks for your patience on this matter. I shall return when the household is fed!
Clive.

I was thinking the same thing.  I'm just down the coast from you.  I leave ubuntuforums on most of the time.

Something for you to think about while cooking dinner.

There is no functional advantage to the host ARTDEMO in having 2 IP addresses to the same machine in the same subnet.  It's the same as having 2 doors to the your den at home on the same side of the room going to the same hallway.  My first inclination is to down the wireless interface, but if you like you can disable the wired one and we can test from there.

In all reality you can just reboot now and see if the problem returns while using 1 interface.  Nautilus is kind of like a black box a lot of the time.  Gnome dev's are sort of on their own track.  You are not the first person to wonder about how Nautilus goes about its business.

I have 3 Samba and NFS servers here at home and use a Ubuntu Gnome3 (Unity) and Windows 7 clients and  with no problems at all.  I can add new Samba server and have it show up in the time it takes to install the software and copy my personal smb.conf file to the machine and create the share (about 5 minutes).  Problems like yours are always in the details.  Two interfaces on one host in a subnet is just one of those types of details.

The only reason ARTDEMO is the MB is because you never turn it off.  If you did some other machine would become the MB and that is usually what the delay is that folks talk about,

Back after my dinner.  Yes, I am the chef in my house too!  :D

---

### Post by CliveMcCarthy on 2013-08-03
I lost a post I was composing (the forum timed out on me) but never mind. I disabled the WiFi on ARTDEMO which seems to have killed almost everything! **Smbtree** ends without displaying anything on any of the machines. It seems the response is NT_STATUS_HOST_UNREACHABLE. Which sounds nicely archaic.

NETbios is working so I can still see all the machines on the network. Nautilus seems oblivious to the fact that things have changed at least on the 'blind' machine. Q9550 is rebooted but it is unable to find anything on the network except the Mac...

So now I guess I wait until some other machine gets to be the MB?

---

### Post by Morbius1 on 2013-08-03
This has turned into a very confusing thread. One thing for sure though is this will not work. I can't tell if it's due to multiple routers in the same subnet and multiple nics on the same machines or multiple connections to the same router or what:
> IP address       NetBIOS Name     Server    User             MAC address      
------------------------------------------------------------------------------
192.168.2.24     VOSTROV13        <server>  VOSTROV13        00:00:00:00:00:00
192.168.2.40     VOSTROV13        <server>  VOSTROV13        00:00:00:00:00:00

192.168.2.49     ARTSHOW45        <server>  ARTSHOW45        00:00:00:00:00:00
192.168.2.18     ARTSHOW45        <server>  ARTSHOW45        00:00:00:00:00:00

192.168.2.32     ARTSHOW43        <server>  ARTSHOW43        00:00:00:00:00:00
192.168.2.37     ARTSHOW43        <server>  ARTSHOW43        00:00:00:00:00:00

192.168.2.35     ARTDEMO          <server>  ARTDEMO          00:00:00:00:00:00
192.168.2.33     ARTDEMO          <server>  ARTDEMO          00:00:00:00:00:00

Just out of curiosity and assuming all these machines are Linux what ip address does this command display:
```
getent hosts vostrov13.local
```

---

### Post by bab1 on 2013-08-03
> **CliveMcCarthy said:**
> I lost a post I was composing (the forum timed out on me) but never mind. I disabled the WiFi on ARTDEMO which seems to have killed almost everything! **Smbtree** ends without displaying anything on any of the machines. It seems the response is NT_STATUS_HOST_UNREACHABLE. Which sounds nicely archaic.

I'll bet you really didn't have both wifi and wired on ARTDEMO then.  Usually NT_STATUS_HOST_UNREACHABLE means the host known but is off line.
> 

NETbios is working so I can still see all the machines on the network. 

All of this is NETBIOS, so how can these two statements exist at the same time?
> 
Nautilus seems oblivious to the fact that things have changed at least on the 'blind' machine. Q9550 is rebooted but it is unable to find anything on the network except the Mac...

So now I guess I wait until some other machine gets to be the MB?
If you turn offARTDEMO for a few minutes and try to browse from some other machine (maybe a "seeing" one) you can force an election of a new MB.

I think you have some non standard configuration somewhere.  It shouldn't be this hard to setup Samba.  As a matter of fact the "blind machine" is really acting as a client machine and not a server when you are browsing with it.

Just a thought -- Do you have Winbind installed in this network?

---

### Post by bab1 on 2013-08-03
> **Morbius1 said:**
> This has turned into a very confusing thread. One thing for sure though is this will not work. I can't tell if it's due to multiple routers in the same subnet and multiple nics on the same machines or multiple connections to the same router or what:

I'll bet all of those machines have both wired and wireless interfaces.  My guess is that only 1 interface per machine is actually enabled,  If I remember correctly, the NETBIOS protocol will not allow *active* duplication of COMPUTER NAMES in a network, so something is wrong here.  Maybe it's because  the app used to get this information polls the individual hosts for the information and uses multiple tools to do this.  Note that it can't determine the MAC address of any of these interfaces.
> 

Just out of curiosity and assuming all these machines are Linux what ip address does this command display:
```
getent hosts vostrov13.local
```
i believe that just queries the local hosts /etc/host file for that host name.

---

### Post by Morbius1 on 2013-08-03
```
getent hosts vostrov13.local
```
It should return the ip address of     VOSTROV13.

I want to know if it comes back with an error, 192.168.2.24, or 192.168.2.40.

You can also just ping the darn thing from     ARTDEMO:
```
ping vostrov13.local
```

---

### Post by CliveMcCarthy on 2013-08-03
The __MSBROWSE__ has migrated to ARTSHOW24 which is a wired-only machine. Things have changed a lot since I took ARTDEMO out of the picture so it's hard to make much sense things from earlier postings. The 'good' news is I now have two 'blind' machines. 

I still have two machines on the network that have wired and wireless connections. It is the default behavior of Linux to connect to both network connections, if they are available, though I appreciate it doesn't in any way increase the bandwidth to the machines. **Smbtree** functions on both 'blind' machines after I restarted their services and reports a full list of machines on the network, though Nautilus still does not. In fact Nautilus does not display the lone Mac any longer.

Through all of this there is a consistent problem with the Nautilus-Samba interface: since **smbtree** is showing that Samba is active and able to locate the names and addresses of machines, yet Nautilus does not show them. 


[HR][/HR]
Here are several diagnostic dumps similar to the ones previously posted. I don't think they reveal anything particularly helpful.

```

clive@VostroV13 ~ $ getent hosts vostrov13.local

192.168.2.40    vostrov13.local
clive@VostroV13 ~ $ 

```

```

clive@VostroV13 ~ $ smbclient -L ARTSHOW24
Enter clive's password: 
Domain=[CLIVEWORKGROUP] OS=[Unix] Server=[Samba 3.5.4]


    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (artshow24 server (Samba, Ubuntu))
    print$          Disk      Printer Drivers
    shareddocs      Disk      artshow15 shared
Domain=[CLIVEWORKGROUP] OS=[Unix] Server=[Samba 3.5.4]


    Server               Comment
    ---------            -------
    ARTDEMO              artdemo server (Samba, Ubuntu)
    ARTSHOW15            artshow15 server (Samba, Ubuntu)
    ARTSHOW21            artshow21 server (Samba, Ubuntu)
    ARTSHOW24            artshow24 server (Samba, Ubuntu)
    ARTSHOW33            artshow33 server (Samba, Ubuntu)
    ARTSHOW34            artshow34 server (Samba, Ubuntu)
    ARTSHOW35            artshow35 server (Samba, Ubuntu)
    ARTSHOW43            artshow43 server (Samba, Ubuntu)
    ARTSHOW44            artshow44 server (Samba, Ubuntu)
    ARTSHOW45            artshow45 server (Samba, Ubuntu)
    MACBOOKPRO-AB2A      Tricia Bell's MacBook Pro
    NETFLIX_HD           Zotac Ion
    OPUS38               opus38 server (Samba, LinuxMint)
    Q9550                Q9550 server (Samba, LinuxMint)
    VOSTROV13            VostroV13 server (Samba, LinuxMint)


    Workgroup            Master
    ---------            -------
    CLIVEWORKGROUP       ARTSHOW24
clive@VostroV13 ~ $ 

```

```

clive@VostroV13 ~ $ nbtscan 192.168.2.10-50
Doing NBT name scan for addresses from 192.168.2.10-50


IP address       NetBIOS Name     Server    User             MAC address      
------------------------------------------------------------------------------
192.168.2.11     NETFLIX_HD       <server>  <unknown>        00:01:2e:33:06:ad
192.168.2.28     Q9550            <server>  Q9550            00:00:00:00:00:00
192.168.2.40     VOSTROV13        <server>  VOSTROV13        00:00:00:00:00:00
192.168.2.18     ARTSHOW45        <server>  ARTSHOW45        00:00:00:00:00:00
192.168.2.21     ARTSHOW34        <server>  ARTSHOW34        00:00:00:00:00:00
192.168.2.25     OPUS38           <server>  OPUS38           00:00:00:00:00:00
192.168.2.23     ARTSHOW33        <server>  ARTSHOW33        00:00:00:00:00:00
192.168.2.32     ARTSHOW43        <server>  ARTSHOW43        00:00:00:00:00:00
192.168.2.37     ARTSHOW43        <server>  ARTSHOW43        00:00:00:00:00:00
192.168.2.48     ARTSHOW35        <server>  ARTSHOW35        00:00:00:00:00:00
192.168.2.49     ARTSHOW45        <server>  ARTSHOW45        00:00:00:00:00:00
192.168.2.20     ARTSHOW44        <server>  ARTSHOW44        00:00:00:00:00:00
192.168.2.35     ARTDEMO          <server>  ARTDEMO          00:00:00:00:00:00
192.168.2.42     ARTSHOW21        <server>  ARTSHOW21        00:00:00:00:00:00
192.168.2.46     ARTSHOW15        <server>  ARTSHOW15        00:00:00:00:00:00
192.168.2.30     MACBOOKPRO-AB2A  <server>  <unknown>        60:33:4b:2a:ce:b1
192.168.2.39     BRW0080927F9099  <server>  <unknown>        00:80:92:7f:90:99
clive@VostroV13 ~ $ 

```

```

clive@VostroV13 ~ $ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::224:d6ff:fe21:8f28%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=fe80::226:6cff:fe10:105f%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.2.40 bcast=192.168.2.255 netmask=255.255.255.0
Enter clive's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name CLIVEWORKGROUP<0x1d>
Got a positive name query response from 192.168.2.12 ( 192.168.2.12 )
Connecting to host=192.168.2.12
Connecting to 192.168.2.12 at port 445
Connecting to 192.168.2.12 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.2.12 ( 192.168.2.12 )
name_resolve_bcast: Attempting broadcast lookup for name CLIVEWORKGROUP<0x1d>
Got a positive name query response from 192.168.2.12 ( 192.168.2.12 )
Connecting to host=192.168.2.12
Connecting to 192.168.2.12 at port 445
Connecting to 192.168.2.12 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
CLIVEWORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name CLIVEWORKGROUP<0x1d>
Got a positive name query response from 192.168.2.12 ( 192.168.2.12 )
Connecting to host=192.168.2.12
Connecting to 192.168.2.12 at port 445
Connecting to 192.168.2.12 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\VOSTROV13              VostroV13 server (Samba, LinuxMint)
Connecting to host=VOSTROV13
name_resolve_bcast: Attempting broadcast lookup for name VOSTROV13<0x20>
Got a positive name query response from 192.168.2.40 ( 192.168.2.40 )
Connecting to 192.168.2.40 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\VOSTROV13\HP-LaserJet-1200    HP LaserJet 1200
        \\VOSTROV13\HL2270DW           HL2270DW
        \\VOSTROV13\print$             Printer Drivers
        \\VOSTROV13\shareddocs         
        \\VOSTROV13\music              
        \\VOSTROV13\IPC$               IPC Service (VostroV13 server (Samba, LinuxMint))
    \\Q9550                  Q9550 server (Samba, LinuxMint)
Connecting to host=Q9550
name_resolve_bcast: Attempting broadcast lookup for name Q9550<0x20>
Got a positive name query response from 192.168.2.28 ( 192.168.2.28 )
Connecting to 192.168.2.28 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\Q9550\Brother-HL-2270DW-series    Brother HL-2270DW series
        \\Q9550\print$             Printer Drivers
        \\Q9550\shareddocs         q9550
        \\Q9550\IPC$               IPC Service (Q9550 server (Samba, LinuxMint))
    \\OPUS38                 opus38 server (Samba, LinuxMint)
Connecting to host=OPUS38
name_resolve_bcast: Attempting broadcast lookup for name OPUS38<0x20>
Got a positive name query response from 192.168.2.25 ( 192.168.2.25 )
Connecting to 192.168.2.25 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\OPUS38\print$             Printer Drivers
        \\OPUS38\shareddocs         
        \\OPUS38\IPC$               IPC Service (opus38 server (Samba, LinuxMint))
    \\NETFLIX_HD             Zotac Ion
Connecting to host=NETFLIX_HD
name_resolve_bcast: Attempting broadcast lookup for name NETFLIX_HD<0x20>
Got a positive name query response from 192.168.2.11 ( 192.168.2.11 )
Connecting to 192.168.2.11 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\NETFLIX_HD\SharedDocs         
        \\NETFLIX_HD\IPC$               Remote IPC
    \\MACBOOKPRO-AB2A        Tricia Bell's MacBook Pro
Connecting to host=MACBOOKPRO-AB2A
name_resolve_bcast: Attempting broadcast lookup for name MACBOOKPRO-AB2A<0x20>
Got a positive name query response from 192.168.2.30 ( 192.168.2.30 )
Connecting to 192.168.2.30 at port 445
Doing spnego session setup (blob length=144)
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.752.43.14.3
got OID=1.3.6.1.5.5.14
got OID=1.3.6.1.4.1.311.2.2.10
got OID=1.3.5.1.5.2.7
got OID=1.3.6.1.5.2.5
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x60898235
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
anonymous failed session setup with NT_STATUS_PIPE_BROKEN
    \\ARTSHOW45              artshow45 server (Samba, Ubuntu)
Connecting to host=ARTSHOW45
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW45<0x20>
Got a positive name query response from 192.168.2.18 ( 192.168.2.49 )
Connecting to 192.168.2.49 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW45\shareddocs         artshow15 shared
        \\ARTSHOW45\IPC$               IPC Service (artshow45 server (Samba, Ubuntu))
        \\ARTSHOW45\print$             Printer Drivers
    \\ARTSHOW44              artshow44 server (Samba, Ubuntu)
Connecting to host=ARTSHOW44
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW44<0x20>
Got a positive name query response from 192.168.2.20 ( 192.168.2.20 )
Connecting to 192.168.2.20 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW44\shareddocs         artshow15 shared
        \\ARTSHOW44\IPC$               IPC Service (artshow44 server (Samba, Ubuntu))
        \\ARTSHOW44\print$             Printer Drivers
    \\ARTSHOW43              artshow43 server (Samba, Ubuntu)
Connecting to host=ARTSHOW43
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW43<0x20>
Got a positive name query response from 192.168.2.32 ( 192.168.2.37 )
Connecting to 192.168.2.37 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW43\shareddocs         artshow15 shared
        \\ARTSHOW43\IPC$               IPC Service (artshow43 server (Samba, Ubuntu))
        \\ARTSHOW43\print$             Printer Drivers
    \\ARTSHOW35              artshow35 server (Samba, Ubuntu)
Connecting to host=ARTSHOW35
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW35<0x20>
Got a positive name query response from 192.168.2.48 ( 192.168.2.48 )
Connecting to 192.168.2.48 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW35\shareddocs         
        \\ARTSHOW35\print$             Printer Drivers
        \\ARTSHOW35\IPC$               IPC Service (artshow35 server (Samba, Ubuntu))
    \\ARTSHOW34              artshow34 server (Samba, Ubuntu)
Connecting to host=ARTSHOW34
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW34<0x20>
Got a positive name query response from 192.168.2.21 ( 192.168.2.21 )
Connecting to 192.168.2.21 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW34\shareddocs         
        \\ARTSHOW34\print$             Printer Drivers
        \\ARTSHOW34\IPC$               IPC Service (artshow34 server (Samba, Ubuntu))
    \\ARTSHOW33              artshow33 server (Samba, Ubuntu)
Connecting to host=ARTSHOW33
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW33<0x20>
Got a positive name query response from 192.168.2.23 ( 192.168.2.23 )
Connecting to 192.168.2.23 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW33\shareddocs         
        \\ARTSHOW33\IPC$               IPC Service (artshow33 server (Samba, Ubuntu))
        \\ARTSHOW33\print$             Printer Drivers
    \\ARTSHOW24              artshow24 server (Samba, Ubuntu)
Connecting to host=ARTSHOW24
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW24<0x20>
Got a positive name query response from 192.168.2.12 ( 192.168.2.12 )
Connecting to 192.168.2.12 at port 445
Connecting to 192.168.2.12 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW24\shareddocs         artshow15 shared
        \\ARTSHOW24\print$             Printer Drivers
        \\ARTSHOW24\IPC$               IPC Service (artshow24 server (Samba, Ubuntu))
    \\ARTSHOW21              artshow21 server (Samba, Ubuntu)
Connecting to host=ARTSHOW21
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW21<0x20>
Got a positive name query response from 192.168.2.42 ( 192.168.2.42 )
Connecting to 192.168.2.42 at port 445
Connecting to 192.168.2.42 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW21\shareddocs         artshow15 shared
        \\ARTSHOW21\print$             Printer Drivers
        \\ARTSHOW21\IPC$               IPC Service (artshow21 server (Samba, Ubuntu))
    \\ARTSHOW15              artshow15 server (Samba, Ubuntu)
Connecting to host=ARTSHOW15
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW15<0x20>
Got a positive name query response from 192.168.2.46 ( 192.168.2.46 )
Connecting to 192.168.2.46 at port 445
Connecting to 192.168.2.46 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ARTSHOW15\shareddocs         artshow15 shared
        \\ARTSHOW15\print$             Printer Drivers
        \\ARTSHOW15\IPC$               IPC Service (artshow15 server (Samba, Ubuntu))
    \\ARTDEMO                artdemo server (Samba, Ubuntu)
Connecting to host=ARTDEMO
name_resolve_bcast: Attempting broadcast lookup for name ARTDEMO<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ARTDEMO<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ARTDEMO<0x20>
resolve_wins: Attempting wins lookup for name ARTDEMO<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ARTDEMO<0x20>
resolve_hosts: getaddrinfo failed for name ARTDEMO [No address associated with hostname]
cli_start_connection: failed to connect to ARTDEMO<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
clive@VostroV13 ~ $ 

```

---

### Post by Morbius1 on 2013-08-03
Now go to  ARTDEMO open up a terminal and type:
```
nautilus smb://vostrov13.local
```
Does it or does it not connect to vostrov13?
[COLOR=#0000cd][B]EDIT: And can you do it in reverse:

From vostrov13 can you connect to artdemo:[/B][/COLOR]
```
 nautilus smb://artdemo.local
```

---

### Post by CliveMcCarthy on 2013-08-03
ARTDEMO is not one of the 'blind' machines. But VOSTROV13 and Q9550 are.

So I ran **caja smb://ARTSHOW24** from VOSTROV13 (caja is the Mint flavor of Nautilus, as you probably know) and it successfully launched a window showing the shares on ARTSHOW24. However, the network view from Caja/Nautilus shows nothing.
How can I restart Nautilus without rebooting the machine? That might more clearly reveal the issue that I think exists between Nautilus and Samba. Restarting **smbd** and **nmbd** doesn't fix things so I think Samba isn't at fault. Moreover **smbtree** is showing good stuff which Nautilus fails to pick up.

---

### Post by CliveMcCarthy on 2013-08-03
I just tried **caja smb:///** which then launched a window revealing CLIVEWORKGROUP and subsequently all of the machines. However, if I return to Caja/Nautilus and hit reload <Ctrl+R> the network still appears empty!

---

### Post by Morbius1 on 2013-08-03
I don't know why you aren't answering my questions.

I want to know if a "blind" machine can access one that is not blind and vice versa.

I don't want it a smb://artdemo I want it as smb://artdemo.local since it appears as though the avahi process can dtermine the correct ip address.

---

### Post by CliveMcCarthy on 2013-08-03
Morbius,
It is evident to me that the machines CAN see one another, just not through the Caja/Nautilus Network view.
We probably have cross-posting happening.

---

### Post by Morbius1 on 2013-08-03
>  Supplemental: If I look inside the** Windows Network** all the added machines can be seen! 				
This is no longer true?

---

### Post by CliveMcCarthy on 2013-08-03
I just tried **Nautilus smb:///** from ARTSHOW45 (an Ubuntu 10.10 machine) and it can see CLIVEWORKGROUP, VOSTROV13 and the shares VOSTROV13 has :D
I have tried **Caja  smb:/// **from  VOSTROV13 and it can see CLIVEWORKGROUP, ARTSHOW45 and the shares ARTSHOW45 has :D

BUT Caja/Nautilus remains 'blind' on VOSTROV13 when I use the regular Network view :(

I shall reboot Q9550 to see if that removes its Caja/Nautilus blindness.

---

### Post by CliveMcCarthy on 2013-08-03
Yep, rebooting Q9550 causes Caja/Nautilus to clean up its act and show the whole network. Samba was working just fine.

---

### Post by bab1 on 2013-08-03
> **CliveMcCarthy said:**
> Yep, rebooting Q9550 causes Caja/Nautilus to clean up its act and show the whole network. Samba was working just fine.

Rebooting may not be the permanent answer though.  This just means that this machine has re-announced it's presence via broadcasting and has been re-added to the MB list.  As you have said, sometimes it works and sometimes not.

---

### Post by Morbius1 on 2013-08-03
>  BUT Caja/Nautilus remains 'blind' on VOSTROV13 when I use the regular Network view :sad:

@bab1, have you been able to figure out if by "blind" he means it's not showing up when he selects Network but may be visible if he goes to "Windows Network":
> Supplemental: If I look inside the Windows Network all the added machines can be seen!
If he consistently wants it to show up in Network instead of ( or in addition to ) "Windows Network" I've already given him instructions.

---

### Post by bab1 on 2013-08-03
> **Morbius1 said:**
> @bab1, have you been able to figure out if by "blind" he means it's not showing up when he selects Network but may be visible if he goes to "Windows Network":

I can't really tell where the OP is.  I have trouble decoding non standard terms.  
> 

If he consistently wants it to show up in Network instead of ( or in addition to ) "Windows Network" I've already given him instructions.
I think you have explained it well.  From here on in we may be just going 'round in circles if we can't establish a baseline of performance.

---

### Post by Morbius1 on 2013-08-03
Well, I can tell you what I'm talking about. This is how caja looks when you select "Browse Network":
[ATTACH=CONFIG]245044[/ATTACH]
The mac that he has on his network will show up on this screen outside of the "Windows Network" folder. So my question is does "blind" mean it doesn't show up here or does blind mean it doesn't even show up when the "Windows Network" is opened.

I can make all these Linux boxes show up in the Network screen using the exact same mechanism that the Mac is using - regardless if it shows up or not in "Windows Network"

---

### Post by CliveMcCarthy on 2013-08-03
Bab1, Morphius1,
By 'blind' I means Network, not Windows Network.

I shall be traveling for the next week so this thread will have to wait until I return. Thank you both for your help, thus far.
Clive.

---

### Post by bab1 on 2013-08-03
> **Morbius1 said:**
> Well, I can tell you what I'm talking about. This is how caja looks when you select "Browse Network":
[ATTACH=CONFIG]245044[/ATTACH]

I understood what you meant.  I have seen where others are surprised to see the Samba servers inside the "Windows Network".  Maybe a poor name choice.  More like **"SMB/CIFS Windows type network".**  In any case there have been cases where a machine I have added or reconfigured not show up in the "Network" view unless you drilled down inside the "Windows Network".  Eventually they show up.  These are all just view s of the same thing anyway.  These views are all Nautilus (Gnome) things.  Like you, I'm interested if the Sanba servers show up at all either in the basic Network view or under the "Windows Network" icon.  
> 
The mac that he has on his network will show up on this screen outside of the "Windows Network" folder. So my question is does "blind" mean it doesn't show up here or does blind mean it doesn't even show up when the "Windows Network" is opened.

It should be under the "Windows Network" icon also I believe.  It is after all a** "SMB/CIFS Windows Type Shares"** server at heart too.
> 

I can make all these Linux boxes show up in the Network screen using the exact same mechanism that the Mac is using - regardless if it shows up or not in "Windows Network"
Mine show up in both places as they are different views of the same thing; right?

---

### Post by bab1 on 2013-08-03
> **CliveMcCarthy said:**
> Bab1, Morphius1,
By 'blind' I means Network, not Windows Network.

I shall be traveling for the next week so this thread will have to wait until I return. Thank you both for your help, thus far.
Clive.
Bingo!  It is not blind at all.  Maybe misguided is a better word.  If they are there under the "Windows Network" view then the system is working and they will eventually show up along side in the "Network" view.

---

### Post by Morbius1 on 2013-08-03
Sometimes it pays to take users posts literally :)

I'm thinking there is nothing to fix here since "Windows Network" is synonymous with Samba Network. 

You can use the method I mentioned at the start of this topic but it's going to get confusing since you will have for example "Samba ARTSHOW45" show up under "Network" and "ARTSHOW45" show up under "Windows Network" and if the moon is in the correct alignment you may even have  ARTSHOW45 show up under Network next to "Samba ARTSHOW45". 

This is how I run my little zoo but confusion is my middle name.

---

### Post by bab1 on 2013-08-03
> **Morbius1 said:**
> Sometimes it pays to take users posts literally :)

I'm thinking there is nothing to fix here since "Windows Network" is synonymous with Samba Network. 

You can use the method I mentioned at the start of this topic but it's going to get confusing since you will have for example "Samba ARTSHOW45" show up under "Network" and "ARTSHOW45" show up under "Windows Network" and if the moon is in the correct alignment you may even have  ARTSHOW45 show up under Network next to "Samba ARTSHOW45". 

This is how I run my little zoo but confusion is my middle name.

++71 ( as in the number of posts in this drama)!!! :D

So "Failed to retrieve share list from server" really has nothing to do with any of this either I guess.

FYI - I rebooted my server and had my laptop take over as the MB.  It took about 25 minutes for the "little devils" to appear alongside the "Windows Network" icon in the Nautilus "Network" view.  All of these are Ubuntu 12.04 hosts.

---

### Post by Morbius1 on 2013-08-03
> **bab1 said:**
> So "Failed to retrieve share list from server" really has nothing to do with any of this either I guess
I don't know as it seems there were multiple things going one here. bcast was changed to be first after all.

---

### Post by bab1 on 2013-08-03
> **Morbius1 said:**
> I don't know as it seems there were multiple things going one here. bcast was changed to be first after all.

Sorry, double post.

---

### Post by bab1 on 2013-08-03
> **Morbius1 said:**
> I don't know as it seems there were multiple things going one here. bcast was changed to be first after all.

Wait, wait...I think he commented it out it I remember correctly.

Edit: See post #37

Back to sleep I go..................

---

### Post by CliveMcCarthy on 2013-08-12
I'm back. Perhaps I have exhausted your patience on this matter, but while I was traveling I made some general notes. They may seem like a rant, but I hope you will excuse the tone.

[HR][/HR]
There are two views provided which leads an innocent user to think that these 
are two independent mechanism. I gather from this thread that they are somehow 
the same but that one is a "SMB/CIFS Windows type network" and the other is 
something else?


What often happens for me is that the non-Windows 'Network' appears and can take a 
long  time before it is populated. Sometimes it can take days but perhaps it 
remains unpopulated forever -- there is no way of knowing -- there is no 
information provided about the progress of the network view.


What is wrong with this is that a user doesn't care what kind of network view is 
being shown. A user simply expects computers that are on the network to show up. 
Having TWO lists which contain the same information is redundant and confusing. 


The Nautilus interface should merge the two views and present a single list. A 
user DOES NOT CARE about the mechanism, unless it goes wrong! And when things do 
go wrong a helpful diagnostic message is necessary.


I will often click on the Windows Network and then get the message:
    "**Failed to retrieve share list from Server**"
What is fundamentally wrong with this message is that it fails to say which 
server, or even which servers, were tried. The user is left in limbo there is no 
diagnostic information at all.


What compounds this, for me, is that I presumed that it was my DHCP server that 
was at fault yet when I would browse the routers address table the ip addresse 
leases for the whole network would be present.


Further, with a little understanding of NetBIOS it became clear that nbtscan 
could be counted upon to very quickly find all the machines names and their ip 
addresses on the network, when Nautilus still couldn't. I can run smbtree and 
likewise find all the machines on the network, but Nautilus still fails to show 
them.


I'm lead to understand that bcast is probably the best mechanism to use in a 
modest sized network, but the fact that it designates a particular (but 
seemingly random) machine as the name server is, for me, a severe problem. In my 
environment machines constantly join and leave the network. I could live with 
the fact that ONE machine served the network, then I'd keep it running all the 
time as a master server, in much the same way I keep the router running for DHCP 
purposes.

---

### Post by Morbius1 on 2013-08-12
I'm not going to go through all that since what you are describing is pretty much how Samba works in it's entirety. In an all Windows environment you have the exact same phenomenon happening. Not all Windows client show up when you first enter a network in that setup either.

Your specific case however is entirely different since in your original post the difficulty was expressed as follows:
> I just can't get a reliable Linux-to-Linux shared network functioning...
Samba between Linux hosts offers the best of both worlds and the answer lies in post #11. With that I no longer need the following to browse to a Samba server:

** Workgroups
** netbios names
** Master Browser
** "name resolve order" is irrelevant
** I don't even have to have nmbd running.

In short it does this because it's using the exact same mechanism as a Mac:
> The curious thing is that the Mac on the network is visible!

Nearly all of the posts on Samba in this or any other forum have to do with the way Windows boxes find each other and how Samba fit's into all of that. Some of the recommendations to resolve the issue are fact-based and others are voodoo-based. In a Linux only or a Linux / Mac / iOS environment you can eliminate all of it.

---

### Post by CliveMcCarthy on 2013-08-12
OK [HTML] http://en.wikipedia.org/wiki/Avahi_(software)[/HTML] I shall do as you recommend and I'll convert to the "miracle of Avahi"  :)
Thanks Morbius...

---

### Post by bab1 on 2013-08-12
> **CliveMcCarthy said:**
> OK [HTML] http://en.wikipedia.org/wiki/Avahi_(software)[/HTML] I shall do as you recommend and I'll convert to the "miracle of Avahi"  :)
Thanks Morbius...

I have a slightly different take on how to configure Samba than @Morbius1 does.  He does have a more pragmatic viewpoint on fixes than I do.  I believe that the reference to what he is recommending is this Linux Mint post: [[COLOR="#FF0099"]http://forums.linuxmint.com/viewtopic.php?f=42&t=112833[/COLOR]]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112833") ...which has this caveat underneath the instructions:
> [I][COLOR="#0000FF"]"Note: In the case of samba it would be better to use the standard samba method and resolve any discovery issues with this HowTo: Samba Browsing Problems Checklist. The samba client is using resources to find the shares anyway so you might as well use it. An avahi announcement of those shares will make it appear faster in nautilus however.
" [/COLOR][/I]

I'm not saying that @Morbius1's method won't work.  He really knows Samba as well as anyone on these forums.  What I am saying is; if it doesn't work it is not the fault of the "fix recommended", more like some Samba support mechanism is not correctly configured.  Avhai does not eliminate the need for SMB/CIFS protocols (e.g Samba). My inclination is to fix the underlying problem, rather than to add to the complexity.

---

### Post by CliveMcCarthy on 2013-08-12
I have set up two machines with **Avhai** and so far so good. Morbius's instructions worked without any difficulty at all.

My guess is that the because **bcast** method relies on a semi-stable name server, albeit a roving one, that my network was being occasionally 'broken' when I had unknowingly removed the **bcast** server from the network, thus throwing the network into confusion.

I was certainly feeling very disappointed with my Linux network when I couldn't solidly maintain Linux-to-Linux shares, yet the lone Mac on the network _always_ showed up!

I shall fire up a bunch of machines as a stress test...

---

### Post by CliveMcCarthy on 2013-08-12
It's not as good as I had hoped...

I have fired up nine or more machines plus four which have the **Avhai** daemon service restarted. The good news is that everything is showing up in the non-Windows network display. The bad news is that when I try to access one machine running **Avhai** from another also running **Avhai** I get a message:

[B]Unable to mount location
Failed to retrieve share list from server: Connection timed out.
[/B]
This is not true for all the **Avhai** machines and not in both directions A can see B but B can't see A. I shall investigate more tomorrow.

---

### Post by bab1 on 2013-08-12
> **CliveMcCarthy said:**
> I have set up two machines with **Avhai** and so far so good. Morbius's instructions worked without any difficulty at all.

My guess is that the because **bcast** method relies on a semi-stable name server, albeit a roving one, that my network was being occasionally 'broken' when I had unknowingly removed the **bcast** server from the network, thus throwing the network into confusion.

There is no name server involved in the bcast method.  Broadcast, by definition, sends the data and or the request to all hosts on the network.  

There is a singular (but not always the same) host that maintains a Master Browse list.  This list is used **only when you browse** the network.  If you look for a *specific* host there is **NO BROWSING** using the Master Browse list.  When you use Nautilus in this fashion```
smb://COMPUTER_NAME/share
```...you are NOT browsing!  When you click on the Computer in the window either next to or under "Windows Network" you are browsing.  These two methods (smb:// vs visual browsing) use different name resolution methods.

It might be helpful for you to understand the processes, before you make assumptions or guesses.  

> 
I was certainly feeling very disappointed with my Linux network when I couldn't solidly maintain Linux-to-Linux shares, yet the lone Mac on the network _always_ showed up!

I shall fire up a bunch of machines as a stress test...
There is also the notion of "client server architecture".   If you are viewing shares from a Linux host and you see the Mac host, you are seeing using a Linux hosted **Samba Client **to view a  Mac hosted **Samba Server**.  Both are Samba.  Both are using the SMB protocol.  Windows also uses SMB for Windows sharing.  They all use the same SMB/CIFS protocol.  The client section of Samba however is not the same as the Samba Server section.

Name services for networks can be very confusing, not to mention the fact that DNS and NETBIOS naming schemes can (and in this case do) coexist on a TCP/IP network.  In addition to all of that, Samba in particular, converts DNS (hosts) names to NETBIOS names unless a specific NETBIOS name is defined in that host's /etc/samba/smb.conf file like this ```
netbios name = <some name>
```...where <some name> is the NETBIOS name you define for the host.

If you do define the NETBIOS name in the /etc/samba/smb.conf file then there is no need for the *nmbd daemon*.  The *nmbd daemon* is specifically there to convert hostnames to NETBIOS names.  So if you have defined it already, the *nmbd daemon* is disabled.

> 
It's not as good as I had hoped...

I have fired up nine or more machines plus four which have the Avhai daemon service restarted. The good news is that everything is showing up in the non-Windows network display. The bad news is that when I try to access one machine running Avhai from another also running Avhai I get a message:

Unable to mount location
Failed to retrieve share list from server: Connection timed out.

This is not true for all the Avhai machines and not in both directions A can see B but B can't see A. I shall investigate more tomorrow. 

So nothing has really changed.  I did the same thing with two of my machines and had no change at all.  It has always been true in my network you could use *smb://hostname.local/share * to locate a specific share anyway.  No modification needed.

I think you should start slowly with 2 Linux machines and configure each of them to work as both clients and servers.  Then add one machine at a time in the beginning.  Adding "nine or more more machines" at one time adds too many variables to the mix to diagnose effectively,  Once you get 2 Linux hosts to work correctly we can add a Windows machine.  We can verify the setup and deal with any problems.  After that we can introduce the Mac host and to the same thing.

Each machine needs to be checked and configured correctly.  Any other method is really just guessing at what is going on.

---

### Post by Morbius1 on 2013-08-13
> **CliveMcCarthy said:**
> It's not as good as I had hoped...

I have fired up nine or more machines plus four which have the **Avhai** daemon service restarted. The good news is that everything is showing up in the non-Windows network display. The bad news is that when I try to access one machine running **Avhai** from another also running **Avhai** I get a message:

[B]Unable to mount location
Failed to retrieve share list from server: Connection timed out.
[/B]
This is not true for all the **Avhai** machines and not in both directions A can see B but B can't see A. I shall investigate more tomorrow.
On whatever machine you are getting that error message run the following command to get a list of all avahi-enabled machines:
```
avahi-browse -at | grep IPv4
```
Does it list all of them?

If not remember that port 5353 needs to be open if you are doing anything with a firewall. 

And remember to click on the right host when you are in the file manager: If you followed post #11 all of the avahi samba hosts should be listed as "[COLOR=#0000cd]Samba[/COLOR] *some-host-name*" to differentiate it from the others.

The future of Samba in the home network belongs to avahi not the netbios mechanism so if there is a problem with it under stress I would like to know. At it's peak I have 12 machines set up this way and have not had a problem but .....

---

### Post by CliveMcCarthy on 2013-08-13
Here's the output from** avahi-browse**
```

clive@VostroV13 ~ $ avahi-browse -at | grep IPv4+   
+   eth0 IPv4 Samba-Avahi G750                              Microsoft Windows Network local
+   eth0 IPv4 Samba Q9550                                   Microsoft Windows Network local
+   eth0 IPv4 Samba-Avahi artshow24                         Microsoft Windows Network local
+   eth0 IPv4 Samba VostroV13                               Microsoft Windows Network local
+   eth0 IPv4 artshow24 [74:f0:6d:8c:36:58]                 Workstation          local
+   eth0 IPv4 artshow21 [48:5d:60:53:fe:1c]                 Workstation          local
+   eth0 IPv4 artshow44 [00:01:2e:31:4e:9a]                 Workstation          local
+   eth0 IPv4 Q9550 [00:1c:c0:8c:36:dc]                     Workstation          local
+   eth0 IPv4 G750 [74:d0:2b:15:fe:63]                      Workstation          local
+   eth0 IPv4 artshow15 [48:5d:60:52:da:ee]                 Workstation          local
+   eth0 IPv4 artshow43 [00:01:2e:31:60:bb]                 Workstation          local
+   eth0 IPv4 artshow45 [00:01:2e:31:60:f5]                 Workstation          local
+   eth0 IPv4 VostroV13 [00:26:6c:10:10:5f]                 Workstation          local
+   eth0 IPv4 Q9550                                         Remote Disk Management local
+   eth0 IPv4 G750                                          Remote Disk Management local
+   eth0 IPv4 VostroV13                                     Remote Disk Management local
+   eth0 IPv4 68:09:27:27:ae:9b@fe80::6a09:27ff:fe27:ae9b   _apple-mobdev._tcp   local
+   eth0 IPv4 Brother HL-2270DW series                      Web Site             local
+   eth0 IPv4 Brother HL-2270DW series                      Internet Printer     local
+   eth0 IPv4 Brother HL-2270DW series                      UNIX Printer         local
+   eth0 IPv4 Brother HL-2270DW series                      PDL Printer          local
+   eth0 IPv4 artdemo [70:f1:a1:89:68:0a]                   Workstation          local
+   eth0 IPv4 artdemo                                       Remote Disk Management local
clive@VostroV13 ~ $ 

```
I have reduced the number of machines on the network by a few.
To keep things somewhat simple I will work with just two VostroV13 and artshow24. I am able to browse VostroV13 from artshow24 but not vice versa.

---

### Post by Morbius1 on 2013-08-13
And when you run the following command:
 ```
nautilus network:///
```
Do you see this:
```
Samba-Avahi artshow24
Samba VostroV13
```

[COLOR=#0000cd]*EDIT: Didn't read your post correctly it's artshow that's the problem so the questions should have been this:*[/COLOR]
And when you click on "Samba-Avahi artshow24" from vostrov  that's when you get a error message or are you clicking on something else.

Can I assume you can still do this from vostrov without error:
```
nautilus smb://artshow24.local
```

---

### Post by CliveMcCarthy on 2013-08-13
nautilus {caja in my case} smb://artshow24.local
yields nothing in the terminal but a dialog box pops up which contains the message:

[B]Error: Failed to retrieve share list from server
Please select another viewer and try again.


[/B]

---

### Post by Morbius1 on 2013-08-13
Can you or can you not see **Samba-Avahi artshow24**

Under "Browse Network" in caja?

Can you even ping the machine from vostrov:
```
ping artshow24.local
```

---

### Post by CliveMcCarthy on 2013-08-13
I _can_ see **Samba-Avahi artshow24** in the nautilus/caja Network list. And ping is OK.

```

clive@VostroV13 ~ $ ping artshow24.local
PING artshow24.local (192.168.2.12) 56(84) bytes of data.
64 bytes from artshow24.local (192.168.2.12): icmp_req=2 ttl=64 time=149 ms
64 bytes from artshow24.local (192.168.2.12): icmp_req=3 ttl=64 time=5.48 ms
64 bytes from artshow24.local (192.168.2.12): icmp_req=4 ttl=64 time=5.37 ms
64 bytes from artshow24.local (192.168.2.12): icmp_req=5 ttl=64 time=153 ms
64 bytes from artshow24.local (192.168.2.12): icmp_req=6 ttl=64 time=70.4 ms
64 bytes from artshow24.local (192.168.2.12): icmp_req=7 ttl=64 time=37.3 ms
64 bytes from artshow24.local (192.168.2.12): icmp_req=8 ttl=64 time=7.22 ms
64 bytes from artshow24.local (192.168.2.12): icmp_req=9 ttl=64 time=5.98 ms
^C
--- artshow24.local ping statistics ---
9 packets transmitted, 8 received, 11% packet loss, time 8016ms
rtt min/avg/max/mdev = 5.372/54.287/153.106/59.863 ms
clive@VostroV13 ~ $ 

```

---

### Post by Morbius1 on 2013-08-13
I am going to run a machine with MATE as the DE to see if I can reproduce this problem. Not sure how I can reproduce the situation of having 2 ip adresses for the same hostname that you have on some of your other machines but maybe it won't come up. This will take a bit.

---

### Post by CliveMcCarthy on 2013-08-13
OK. I have eliminated all the 2 ip address issues from the network and shutdown most of the machines. I should mention that VostroV13 & Q9550 are both running Mint 14 with Mate and that Artshow24 is running Ubuntu 10.10 as is Artshow21. Curiously, I am able to browse Artshow21.



```

clive@VostroV13 ~ $ nbtscan 192.168.2.10-50
Doing NBT name scan for addresses from 192.168.2.10-50

IP address       NetBIOS Name     Server    User             MAC address      
------------------------------------------------------------------------------
192.168.2.11     NETFLIX_HD       <server>  <unknown>        00:01:2e:33:06:ad
192.168.2.28     Q9550            <server>  Q9550            00:00:00:00:00:00
192.168.2.40     VOSTROV13        <server>  VOSTROV13        00:00:00:00:00:00
192.168.2.12     ARTSHOW24        <server>  ARTSHOW24        00:00:00:00:00:00
192.168.2.21     ARTSHOW21        <server>  ARTSHOW21        00:00:00:00:00:00
clive@VostroV13 ~ $ 

```

---

### Post by Morbius1 on 2013-08-13
Ah, but can you access [B]Samba-Avahi artshow24

[/B]BTW, I can't get your exact error message but I do get a stall if I enable the firewall on the server. Did you disable the firewall on artshow24:
sudo ufw disable

**One more edit**, Sorry. There seems to have been a lot of bugs back in 10.10 with avahi. I don't suppose by any chance it's only the 10.10 machines you can't access via avahi?

---

### Post by CliveMcCarthy on 2013-08-13
I am unable to access Samba-Avahi artshow24 from VostroV13, though I can do the reverse.

I ran** ufw disable** on artshow24 but it remains inaccessible.

It so happens that I have two 10.10 machines up and running: artshow21 is almost identical to artshow24 however, I can access 21 but not 24.

I

---

### Post by CliveMcCarthy on 2013-08-13
Things have shifted. I no longer see [COLOR=#000000]**Samba-Avahi artshow24** in the list on VostroV13 at all. Damn.

If I re-start Avahi on [/COLOR][COLOR=#000000]artshow24 things may start working but we will lose the diagnostic focus.[/COLOR]

---

### Post by Morbius1 on 2013-08-13
You shouldn't have to restart avai-daemon. I can change the name to XXX %h in /etc/avahi/services/samba.service and it will show up in the client with the new name - without exaggeration - instantaneously.

Is it only this machine that is not working with avahi or do you have similar problems with others?

---

### Post by CliveMcCarthy on 2013-08-13
I now only have this one 'difficult' machine. Most of the machines, which are now off-line, do not have **Avahi** and are all running 10.10. There were just four machines set up with **Avahi** three of which have more current versions of Ubuntu/Mint. The newer OS machines worked  with **Avahi**, but then they also worked fine without it!

What we are trying to do is nail down an intermittent issue. Over the past several years with 10.10 installed on all machines I would be unable to connect to _various_ machines. Sometimes many, sometimes just a few. Given time, things would 'mend' themselves and run happily for many weeks. Then quit again and present me with that most hated message.

I shall go to artshow24 and edit the Avahi services file and report back...

---

### Post by CliveMcCarthy on 2013-08-13
Yep -- instantaneous it is! However, I still get the damned message from VostroV13.

---

### Post by CliveMcCarthy on 2013-08-13
Here is some kind of clue. Smbtree does not show any resources on artshow24 yet it has a shared folder -- I just checked the folder's sharing permissions. Can Samba distinguish between an empty list and no list?

```
clive@VostroV13 ~ $ smbtree
CLIVEWORKGROUP
    \\VOSTROV13              VostroV13 server (Samba, LinuxMint)
        \\VOSTROV13\HP-LaserJet-1200    HP LaserJet 1200
        \\VOSTROV13\HP-LaserJet-4L     HP LaserJet 4L
        \\VOSTROV13\HL2270DW           HL2270DW
        \\VOSTROV13\print$             Printer Drivers
        \\VOSTROV13\shareddocs         
        \\VOSTROV13\music              
        \\VOSTROV13\IPC$               IPC Service (VostroV13 server (Samba, LinuxMint))
    \\Q9550                  Q9550 server (Samba, LinuxMint)
        \\Q9550\Brother-HL-2270DW-series    Brother HL-2270DW series
        \\Q9550\print$             Printer Drivers
        \\Q9550\shareddocs         q9550
        \\Q9550\IPC$               IPC Service (Q9550 server (Samba, LinuxMint))
    \\NETFLIX_HD             Zotac Ion
        \\NETFLIX_HD\SharedDocs         
        \\NETFLIX_HD\IPC$               Remote IPC
    \\MACBOOKPRO-AB2A        Tricia Bell's MacBook Pro
    \\ARTSHOW40              artshow40 server (Samba, Ubuntu)
        \\ARTSHOW40\shareddocs         artshow15 shared
        \\ARTSHOW40\print$             Printer Drivers
        \\ARTSHOW40\IPC$               IPC Service (artshow40 server (Samba, Ubuntu))
    \\ARTSHOW24              artshow24 server (Samba, Ubuntu)
    \\ARTSHOW21              artshow21 server (Samba, Ubuntu)
        \\ARTSHOW21\shareddocs         artshow15 shared
        \\ARTSHOW21\print$             Printer Drivers
        \\ARTSHOW21\IPC$               IPC Service (artshow21 server (Samba, Ubuntu))
clive@VostroV13 ~ $ 


```

---

### Post by Morbius1 on 2013-08-13
> The newer OS machines worked  with **Avahi**, but then they also worked fine without it!
That's not exactly the question I asked. All Linux and OSX machines will respond to a hostname.local query. This thread is solely about having avahi broadcast the presence of a samba server via /etc/avahi/services/samba.service file so that it shows up under network:/// and can be accessed that way.

The way I set this up all of the machines that have samba.services files in them will broadcast a name that is different from the normal legacy samba way - with a "Samba hostname" in the file manager. What I wanted to know was if only the artshow24 machine is the issue when accessed that way.
>                           Yep -- instantaneous it is! However, I still get the damned message from VostroV13.         
Fascinating.

This post has gone on for so long I don't remember if anyone's asked for this or not. If it has point me to the answer:
Go to the artshow24 machine and post the output of the following command:
```
testparm -s
```
and just in case this one:
```
net usershare info --long
```
*Don't be concerned if you get no output from the second command.*

---

### Post by CliveMcCarthy on 2013-08-13
Will do. Be back soon...

---

### Post by CliveMcCarthy on 2013-08-13
So those two commands reveal:

```

clive@artshow24:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = CLIVEWORKGROUP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
clive@artshow24:~$ 

```
```
clive@artshow24:~$ net usershare info --long
[shareddocs]
path=/home/clive/Desktop/shareddocs
comment=artshow15 shared
usershare_acl=S-1-1-0:F,
guest_ok=y
clive@artshow24:~$ 

```

---

### Post by Morbius1 on 2013-08-13
Well, that's too bad since everything seems to be in order. I was hoping for something more exotic and obviously wrong. Even if the the home directory were encrypted or the permissions were wrong you should still see the print$ share.

BTW, You might want to add the following line under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```
It won't do anything for the samba.service avahi process to function since it won't use it but you never know where this machine will end up.

> Over the past several years with 10.10 installed on all machines I would be unable to connect to _various_ machines. Sometimes many, sometimes just a few. Given time, things would 'mend' themselves and run happily for many weeks.

The thing with this is that the avahi process bypasses all the things about the legacy process that can sometimes cause that to happen. And it appears to be working or else this wouldn't have happened:
> Yep -- instantaneous it is!
There's something else afoot here me thinks. 2 routers both supplying DHCP perhaps?

Did you ever think to upgrade to a newer version? I have some iso's around here but nothing that goes back to 10.10 so trying to reproduce this problem is kind of hard for me.

---

### Post by CliveMcCarthy on 2013-08-13
As perhaps you can tell, these machines are artworks each of which functions as a separate 'canvas' -- I use a relatively standardized set of hardware with an Atom CPU and an Nvidia Ion GPU. The artworks themselves exist on small HDDs which I can plug into various 'frames'. I have quite a large number of drives representing various works. I have started to upgrade from 10.10 to a newer OS. In practice this involves creating a stable master HDD and then cloning the drive with a HDD duplicator, then editing the hostname for the specific work. Upgrading all of the existing HDDs is quite a lot of work.

Here's the latest: **Samba-Avahi-10.10 artshow24** has disappeared from the list. It is just gone from view from Vostrov13 and other machines! Weird.

I will check the routers. I set the system up so that there was only one DHCP server, of course, but something perhaps has defaulted to a reset condition...

---

### Post by Morbius1 on 2013-08-13
You know you might want to try an experiment the next time you need to  reboot artshow24. Boot into a current Mint LiveDVD - not to install it just to  have a live session. Mint already has samba and avahi running in the  live state - you can even create a share from the file manager.

Then see if both the standard samba works and see if this still throws an error:
```
caja smb://mint.local
```

The reason I suggest this is not so much to convince you to update your system but if the exact same thing happens with a more current distro then the problem points to artshow24's place in the topology of the network and nothing to do with samba or avahi.

[COLOR=#0000cd]**EDIT**[/COLOR]: [COLOR=#0000cd]simultaneous posts it seems. Based on your description it's not clear to me that the "device" you are running it from even has a cdrom/dvd.[/COLOR]

---

### Post by CliveMcCarthy on 2013-08-13
Correction: **Samba-Avahi-10.10 artshow24 ****is back again!**

---

### Post by Morbius1 on 2013-08-13
Is this thing on wireless? You aren't connecting in and out of neighbor bob's network are you? :p

---

### Post by CliveMcCarthy on 2013-08-13
Yes, it is wireless but it has a strong signal (-59dBm) from a nearby AP of mine. I'll switch it to wired just for fun.

---

### Post by CliveMcCarthy on 2013-08-13
Switched artshow24 to wired but VostroV13 still shows: [COLOR=#000000]**Failed to retrieve share list from server** when browsing artshow24

[/COLOR]

---

### Post by CliveMcCarthy on 2013-08-13
It's the same.

---

### Post by Morbius1 on 2013-08-13
> **CliveMcCarthy said:**
> Switched artshow24 to wired but VostroV13 still shows: [COLOR=#000000]**Failed to retrieve share list from server** when browsing artshow24

[/COLOR]
I hate to be persistent about this but did you get that error message when trying to access artshow24 or **Samba-Avahi-10.10 artshow24?**

---

### Post by CliveMcCarthy on 2013-08-13
Actually both. **Samba-Avahi-10.10 artshow24 **certainly does it. I just tried it again just a second ago.

I just checked the three wireless APs that I have, only one of which is capable of being DHCP server. I have its DHCP turned off. Only the main gateway router is enabled to act as a DHCP server.

---

### Post by CliveMcCarthy on 2013-08-13
I ran smbtree on artshow24 and got this:

```

CLIVEWORKGROUP    
        \\VOSTROV13              VostroV13 server (Samba, LinuxMint)
        \\VOSTROV13\HP-LaserJet-1200    HP LaserJet 1200
        \\VOSTROV13\HP-LaserJet-4L     HP LaserJet 4L
        \\VOSTROV13\HL2270DW           HL2270DW
        \\VOSTROV13\print$             Printer Drivers
        \\VOSTROV13\shareddocs         
        \\VOSTROV13\music              
        \\VOSTROV13\IPC$               IPC Service (VostroV13 server (Samba, LinuxMint))
    \\Q9550                  Q9550 server (Samba, LinuxMint)
        \\Q9550\Brother-HL-2270DW-series    Brother HL-2270DW series
        \\Q9550\print$             Printer Drivers
        \\Q9550\shareddocs         q9550
        \\Q9550\IPC$               IPC Service (Q9550 server (Samba, LinuxMint))
    \\OPUS44                 opus44 server (Samba, LinuxMint)
        \\OPUS44\print$             Printer Drivers
        \\OPUS44\shareddocs         
        \\OPUS44\IPC$               IPC Service (opus44 server (Samba, LinuxMint))
    \\NETFLIX_HD             Zotac Ion
        \\NETFLIX_HD\SharedDocs         
        \\NETFLIX_HD\IPC$               Remote IPC
    \\G750                   G750 server (Samba, LinuxMint)
        \\G750\print$             Printer Drivers
        \\G750\shareddocs         G750
        \\G750\IPC$               IPC Service (G750 server (Samba, LinuxMint))
    \\ARTSHOW40              artshow40 server (Samba, Ubuntu)
        \\ARTSHOW40\shareddocs         artshow15 shared
        \\ARTSHOW40\print$             Printer Drivers
        \\ARTSHOW40\IPC$               IPC Service (artshow40 server (Samba, Ubuntu))
**[COLOR=#ff0000]    \\ARTSHOW24              artshow24 server (Samba, Ubuntu) [/COLOR]****[COLOR=#ff0000]cli_start_connection: failed to connect to ARTSHOW24<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED[/COLOR]**
    \\ARTSHOW21              artshow21 server (Samba, Ubuntu)
        \\ARTSHOW21\shareddocs         artshow15 shared
        \\ARTSHOW21\print$             Printer Drivers
        \\ARTSHOW21\IPC$               IPC Service (artshow21 server (Samba, Ubuntu))
clive@artshow24:~$ 

```

It seems artshow24 won't even connect to its own share!

---

### Post by Morbius1 on 2013-08-13
The server has only one share and it's in your home directory. Did you encrypt your home directory?

---

### Post by CliveMcCarthy on 2013-08-13
From VostroV13 I ran** smbtree -d3** and got:
```

    \\ARTSHOW24              artshow24 server (Samba, Ubuntu)
Connecting to host=ARTSHOW24
name_resolve_bcast: Attempting broadcast lookup for name ARTSHOW24<0x20>
Got a positive name query response from 192.168.2.19 ( 192.168.2.19 )
Connecting to 192.168.2.19 at port 445
Connecting to 192.168.2.19 at port 139
Error connecting to 192.168.2.19 (Connection refused) cli_start_connection: failed to connect to ARTSHOW24<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED

```

---

### Post by CliveMcCarthy on 2013-08-13
The home directory is not encrypted.

---

### Post by Morbius1 on 2013-08-13
Let's rule out any security or permissions problems on artshow24:
```
caja smb://192.168.2.19
```
What errors now?

---

### Post by CliveMcCarthy on 2013-08-13
[B]A dialog box pops up with:

Could not display "smb://192.168.2.19/".[/B]
Error: Failed to retrieve share list from server
Please select another viewer and try again.

---

### Post by Morbius1 on 2013-08-13
The "could not display" phrase is throwing me. Do you have the following package on the client:
```
sudo apt-get install gvfs-backends
```
Can you try one more thing please. Access it this way:
```
caja smb://clive@192.168.2.19
```
[COLOR=#0000cd]**EDIT**[/COLOR]: As much as I hate to do this - and I truly mean that - I have to end it for the day. If I post anymore at this point in the day it will likely be random letters. There is no purer way to access another machine than by ip address so something fundamental is amiss.

---

### Post by CliveMcCarthy on 2013-08-13
gvfs-backends is already installed.

The response to [COLOR=#000000][FONT=Ubuntu Mono]**caja smb://clive@192.168.2.19** is identical to the previous method.

[/FONT][/COLOR]**Could not display "smb://192.168.2.19/".**
Error: Failed to retrieve share list from server
Please select another viewer and try again.
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by CliveMcCarthy on 2013-08-13
Sure. I understand. It's midnight where you are. This is a weird problem...

---

### Post by CliveMcCarthy on 2013-08-13
For tomorrow:

I tried to create a second share on artshow24 but it won't let me. The dialog box asks if Samba is running. I wonder if I should restart smdb on artshow24?

---

### Post by bab1 on 2013-08-13
> **CliveMcCarthy said:**
> For tomorrow:

I tried to create a second share on artshow24 but it won't let me. The dialog box asks if Samba is running. I wonder if I should restart smdb on artshow24?

If the smbd daemon is not running then you will get```

Error connecting to 192.168.2.19 (Connection refused) cli_start_connection: failed to connect to ARTSHOW24<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED

```...along with the inability to create shares (e.g to directly interact with the Samba server on ARTSHOW24).

To check if the server is running you can do this```
ps -ef | grep mbd
```

---

### Post by CliveMcCarthy on 2013-08-14
My interpretation, from your suggestion, is that Samba is NOT running on artshow24.

```

clive@artshow24:~$ ps -ef | grep mbd
root      1322     1  0 Aug12 ?        00:00:03 nmbd -D
clive    11567 10682  0 21:38 pts/2    00:00:00 grep --color=auto mbd
clive@artshow24:~$ ps -ef | grep smbd
clive    11569 10682  0 21:39 pts/2    00:00:00 grep --color=auto smbd
clive@artshow24:~$ ps -ef | grep nmbd
root      1322     1  0 Aug12 ?        00:00:03 nmbd -D
clive    11571 10682  0 21:40 pts/2    00:00:00 grep --color=auto nmbd
clive@artshow24:~$ 

```

It isn't at all clear _why_ but it explains the symptoms.

---

### Post by Morbius1 on 2013-08-14
So the question is did it just stop on it's own in mid session or did it never start or did it try to start too early.

If it's the latter two one way around this is to create a script:
```
gksu gedit /etc/network/if-up.d/smbd-start
```
With this content:
```
#!/bin/sh
start smbd
```
[COLOR=#0000cd]*Make sure there are no spaces in front of the #! line.*[/COLOR]

Make the file executable:
```
sudo chmod +x /etc/network/if-up.d/smbd-start
```

Anything placed in if-up.d will execute only after the network is up.

In later releases this was fixed in the upstart job that starts it by making sure it was started only after the network was up.

---

### Post by CliveMcCarthy on 2013-08-14
I've confirmed that Samba was NOT running on artshow24. I tried **service smbd restart** and got a message that there was no 'instance'. Then I ran **service smbd start**. The machine is now behaving itself on the network. Thank you for your suggested fix. My hypothesis is that the network-Samba race condition has been affecting my 10.10 machines for years, which explains the erratic nature of the problem I have experienced.

I had a similar race condition with my artwork, which uses the entire screen without any task-bar decorations. Mostly it worked, but on rare occasions the task-bars would turn up _after_ the artwork was running. The artwork is launched by a bash script in the start sequence -- I simply added a 3 second delay to allow the task-bar decorations to appear before my code took over the screen.

I guess it is time to upgrade to 13.04 even though it is a good deal of work...

Morbius, Bab, thank you for your help and patience. :popcorn:

---

### Post by Morbius1 on 2013-08-14
> **CliveMcCarthy said:**
> I've confirmed that Samba was NOT running on artshow24. I tried **service smbd restart** and got a message that there was no 'instance'. Then I ran **service smbd start**. 
There was an awkward period where someone from the language police stepped it and declared that if something wasn't started you shouldn't be able to restart it so you got the "no instance" error message.

That was subsequently fixed in later releases as well. It will still give you the error message on the stop part but then it starts it the way it should. Must have been a compromise.[IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]

---

### Post by CliveMcCarthy on 2013-08-14
[SIZE=3]Your comment puts me in mind of a New Yorker cartoon by Richard Cline which has the caption: "People shouldn't get married unless they've been married."
[/SIZE][COLOR=#000000][FONT=Helvetica Nueve][SIZE=3]
[HTML]http://www.condenaststore.com/-sp/People-shouldn-t-get-married-unless-they-ve-been-married-New-Yorker-Cartoon-Prints_i8539564_.htm[/HTML]

I have just fired up another machine with Avahi -- I really like how things change instantly -- it confers a great sense of confidence in the network.


[/SIZE]
[/FONT][/COLOR]

---

