---
title: "Jaunty, wicd and an un-encrypted institutional network"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by gorcq on 2009-10-29
I should like to explain how I solved an incredibly annoying problem with a completely irrational solution after much annoyance. My reasons for writing this are three-fold: First, I am inordinately proud of the solution, despite that it is irrational. Second, while doing some of the research that led to the solution, I formed the impression that many people had this problem and few were finding solutions; therefore, someone may benefit from this. And third, as I have already mentioned, the solution is completely irrational, and I would be very interested in hearing from anyone who claims to be able to explain why it works. I will occasionally check this thread in case such an explanation appears.

Last weekend, I upgraded my laptop from gutsy to jaunty, by which I mean that I installed jaunty over the old installation. There were various problems, as one expects from any new system (unless one is an idiot), but the one that I have been working on since then has been connecting to the wireless network at the university I go to. Connecting to the WEP-encrypted wireless router at my home did not pose any problem at all, but whatever-the-hell program came with jaunty wouldn't connect to the wireless hubs as school.

Now, I had a very similar problem when I first installed gutsy which, on the advice of someone on this forum, I solved by installing a replacement for the network manager called wicd, which I believe stands for WIreless Connection Daemon or something. I immediately thought to fix it the same way this time, but that did not help at all. Wicd would stop when it got to the part where it tries to get an IP address, and not do anything else.

Based upon the logs wicd was generating (see attached file), I came to the conclusion that it was not making contact with the DHCP server on campus. This is bizarre, because it used DHCP to connect to the router at my home, and as I have already stated, it accomplished that with no trouble. That would sort of make it a problem with dhclient, the program wicd uses for DHCP stuff, rather than wicd itself.

I put a message about this on the wicd forum nonetheless, despite that there were many similar threads there already, most un-answred as mine proved to be. I then began searching that forum and the internet for information about similar problems, and tried a variety of stuff, some on advice of dubious reliability. Among other things, I attempted to get a connection from the command line (nil), I installed and set wicd to use an alternate DHCP program called dhcpcd (caused wicd to connect and immediately disconnect then try again repeatedly), I ran various programs I had never heard of (nothing), I upgraded to a slightly newer version of wicd (caused various other problems, so I downgraded again).

On the advice of [some guy](http://wicd.net/punbb/viewtopic.php?id=584), I also tried setting wicd to connect WEP passphrase "    " (that's four space characters), despite that I knew the network to be unencrypted. This was arguably the best yet, because I was able to connect to the network; however, this institution has a policy requiring students to register their laptops with a central server in order to use the network. The only place I could go online was to that server, and it refused to register me, preferring to let me go through the process and then send a page with the word "ERROR" in excessively large, red letters.

Assuming this to be a problem with the college's systems, I went to the local IT area to ask about it. After about half an hour, the upshot was that they were able to register my computer manually, and verify that it was registered, and that didn't help. Their best guess was that the spurious WEP passphrase I was using was somehow screwing things up, but that didn't help much because without it I couldn't connect at all.

I then decided to ask for help on this forum, as the wicd forum seemed non-responsive. In preparation for that, I began to compile a text file of command line output that I thought might potentially be useful to anyone online who might consider helping. I put in the log file entries wicd made after connecting with the passphrase, then I took that out in order to get the entries it generated when it failed to connect at all.

Instead of doing that, it began connecting and disconnecting repeatedly, from which I realized that I still had it set to use dhcpcd for DHCP purposes. So I copied in the log file entries anyway, then set it back to dhclient and got some log file entries with it failing utterly; and realized that I had never yet tried using a spurious WEP passphrase AND dhclient at the same time. And damned if that didn't solve the problem entirely. I am now able to get online and go to websites other than the university's central machine-registration server.


This is much longer than I expected it to be, so I will summarize: [COLOR=blue][FONT=serif][SIZE="3"]When my laptop wouldn't connect to the university's un-encrypted network, I was able to make it do so by setting it to connect using a WEP passphrase consisting in four spaces and using dhclient and NOT dhcpcd for DHCP purposes. There's a setting for that in the wicd preferences.[/SIZE][/FONT][/COLOR]

I am attaching the file with largely-unedited log entries anyway, in case it is of interest to someone.

---

### Post by andersja on 2009-12-07
Thank you for your thorugh walk-through!

I recently set up a laptop for a relative, intending to connect it to a local un-encrypted wifi network where she was. Using wicd, I tested the laptop extensively at my home before handing it over (on a WPA protected wifi network -- no problems). Once in place at its final destination, I too have been seeing bizarre, erratic wicd behaviour - mainly connecting to unencrypted wifi networks, seemingly getting an IP address, then no connection at all...

I will try your 4 spaces hack (although clearly there's a bug to be raised for wicd here? 

I suggest you open a terminal and type:
```
ubuntu-bug wicd
```
- this will gather loads of relevant logs and information for the developers.

Once submitted, (feel free to link to this forum thread too) make sure you also link it to the "upstream" bugtracker at [https://bugs.launchpad.net/wicd/](https://bugs.launchpad.net/wicd/)

---

### Post by andersja on 2009-12-07
@gorcq - I've also seen others recommend wifi-radar where wicd has issues (it appears unencrypted network "roaming" is a particular weakness of wicd). I will try that too. 

Last but not least there is a package called getwifi which dows it all on command line. ( [http://getwifi.sourceforge.net/index.html](http://getwifi.sourceforge.net/index.html) ) 

I haven;t tested either of these yet, but if you do, please share your experiences!

---

