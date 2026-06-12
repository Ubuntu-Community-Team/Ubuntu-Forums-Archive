---
title: "Firewire after upgrade to .21"
date: 2008-03-16
forum: Mythbuntu
---

### Post by dmfrey on 2008-03-16
After upgrading to .21, I am seeing that firewire is being handled differently.

I noticed that a recording failed on my firewire connection.  For the duration of the recording, the logs indicated that it was trying to reset the connection after so many seconds.  I understand that these were some of the changes with myth .21.

I also get that firewire can sometimes be unreliable.  However, I have been running for moths without a missed recording with mythbuntu.

To help counter the unreliability, i tried to enable the firewire priming in the myth-backend init script (set ENABLE_FIREWIRE to TRUE in /etc/default/myth-backend).  I do not believe the mythprime script is accurately detecting the firewire node.  My Motorola DCT-6200 always seems to get onto node 2.  mythprime only appears to be checking node 1.  This fails repeatedly and mythbackend never comes back up since the node it should be checking is 2.  If i disable the priming, and restart the mythbackend,  I can get a connection on node 2, but it appears to be unreliable.

Any thoughts on how to resolve the priming issue?

---

### Post by volkswagner on 2008-03-16
Check here for the documents on priming.

[https://help.ubuntulinux.org/community/MythTV_Firewire]("https://help.ubuntulinux.org/community/MythTV_Firewire")


Toward the bottom of the page see:

> If your STB runs on node 0, port 1 (which seems to be the default node choice for this box), then you only need to compile the primer. If you need to change the port or node for your system, the two locations are clearly commented in main() at the tail of the file myth_prime.c:

    *

      int main(void) {

          raw1394handle_t handle;     // our firewire handle...
          int port = 0;               // port 0
          int node = 1;               // node 1 is default for 62xx (?)
      ...      


Edit accordingly.

Good luck!

---

### Post by dmfrey on 2008-03-16
Thank you volkswagner.

I have read that page.  I guess I am wondering how relevant that page is now that .21 is out?

---

### Post by rhpot1991 on 2008-03-17
There is a mythprime included in the 0.21 packages already, but it is compiled against the default port and node.  It is possible that your system is using this instead of one you were previously using.  See this bug: [https://bugs.launchpad.net/mythbuntu/+bug/201695](https://bugs.launchpad.net/mythbuntu/+bug/201695)

For the time being it is best to just recompile a new version until this gets fixed, and watch for updates that may replace this on you.

---

### Post by 4dognight on 2008-03-17
I am going to be upgrading to .21 here soon, and am surprised that mythprime is still hardcoded on the node you configure it for. I think it should be able to dynamically determine the port and adjust accordingly.  I find it hard to beleive it cant be made dynamic. I was hoping .21 fixed this, but looks like Im going to have to fix this myself, as I found it rather annoying when I would reboot and the node changed.

---

### Post by dmfrey on 2008-03-17
4dognight,

mythprime isn't hardcoded to a firewire node as in you set one from the myth interface.  This was how it used to be pre-.21.  That option is no longer available on the capture card screen.

However, the mythprime binary. when used to prime the firewire port in the init script is hardcoded to node 1.  I haven't had a chance to locate the source yet to see why it is hardcoded to 1.

---

### Post by 4dognight on 2008-03-18
> **dmfrey said:**
> 4dognight,

mythprime isn't hardcoded to a firewire node as in you set one from the myth interface.  This was how it used to be pre-.21.  That option is no longer available on the capture card screen.

However, the mythprime binary. when used to prime the firewire port in the init script is hardcoded to node 1.  I haven't had a chance to locate the source yet to see why it is hardcoded to 1.

I am a bit confused here. I think what you were trying to say is that the firewire node isn't hard coded in the myth setup, but it still is in mythprime.  If that is the case, then thats pretty much what I was saying too.  Firewire in .20 worked, but it was pretty much a pain, with the changing of the node. My wife is boycotting Myth, pretty much based on the flakyness of firewire. Im hoping for a much more solid experience with .21 and firewire. The other annoying side effect with firewire has to do with changing of the channel to a copy protected channel. Myth would update the last channel  in the config, THEN try changing to the channel. If this was a copy protected channel, you were screwed and had to go into the config to move it off that channel. I felt that it should only update the last channel in the config, AFTER a succesful change to the channel. That way, if you fail to change to that channel, it would put you back on the last channel, which obviously was a good channel.

---

### Post by majoridiot on 2008-03-18
> **dmfrey said:**
> Thank you volkswagner.

I have read that page.  I guess I am wondering how relevant that page is now that .21 is out?

the relevance of that page is unknown at this time.  i am the original author and maintainer of the 
firewire guide and only just became aware that significant changes were  made to ubuntu/mythbuntu
mythtv firewire a couple of days ago, when someone pm'd me in confusion.

i am not running the latest updates on my system yet, so i need an opportunity to look into it
further.  i have contacted superm1 about this and he confirmed that significant (and positive!) 
changes were made.  i am expecting more specific info from him soon.  as soon as things 
are sussed as to the current state of firewire, i will make the required changes to the firewire 
guide.  in the meantime, i have posted a note at the head of that page.

sorry for the confusion, folks... but i had no idea these changes were being made.

> **4dognight said:**
> I am a bit confused here. I think what you were trying to say is that the firewire node isn't hard coded in the myth setup, but it still is in mythprime.  If that is the case, then thats pretty much what I was saying too.  Firewire in .20 worked, but it was pretty much a pain, with the changing of the node. My wife is boycotting Myth, pretty much based on the flakyness of firewire. Im hoping for a much more solid experience with .21 and firewire. The other annoying side effect with firewire has to do with changing of the channel to a copy protected channel. Myth would update the last channel  in the config, THEN try changing to the channel. If this was a copy protected channel, you were screwed and had to go into the config to move it off that channel. I felt that it should only update the last channel in the config, AFTER a succesful change to the channel. That way, if you fail to change to that channel, it would put you back on the last channel, which obviously was a good channel.

all you should need to do is get the primer source code from the page, edit the port and node,
recompile and copy it to /usr/bin per the instructions in the guide.  part of what needs to be
handled in the future, per superm1, is configuring the correct port and node on install- since it
*is* currently hard-coded in the source.  when i get more details, this will be addressed as well.

in the meantime, thank you for your patience. ;)

---

### Post by rhpot1991 on 2008-03-18
I can confirm that replacing mythprime with one compiled with the correct port and node "works" with 0.21.  If your box uses the default port and node then technically you don't need to do anything, but if it doesn't you will need to replace mythprime every time the backend gets upgraded.

I say "works" because my box does not lock all the channels that it should, though I just started using firewire with 0.21 a few weeks ago and didn't not have any experience before that so I am not really sure what the issue is.

---

### Post by majoridiot on 2008-03-18
> **rhpot1991 said:**
> I can confirm that replacing mythprime with one compiled with the correct port and node "works" with 0.21.  If your box uses the default port and node then technically you don't need to do anything, but if it doesn't you will need to replace mythprime every time the backend gets upgraded.

fixing mythprime will **not** be necessary every time you upgrade, once the needed runtime 
changes are made to the packages.  this will only be necessary for the near term.  it will all be 
sorted and seamless in the long run. :)

> **rhpot1991 said:**
> I say "works" because my box does not lock all the channels that it should, though I just started using firewire with 0.21 a few weeks ago and didn't not have any experience before that so I am not really sure what the issue is.

i recommend taking a look at the "tips on priming" and "general firewire notes" section of the guide.  it
sounds to me like the channels you can't "lock on" to are likely copy-protected with a CCI of 0x02.

---

### Post by rhpot1991 on 2008-03-18
> **majoridiot said:**
> fixing mythprime will **not** be necessary every time you upgrade, once the needed runtime 
changes are made to the packages.  this will only be necessary for the near term.  it will all be 
sorted and seamless in the long run. :)
That is what I meant, the package will constantly replace yours with a new one that has the default ports until the bug is resolved.  There is also a bug out there to get the p2p primer added as well.


> **majoridiot said:**
> 
i recommend taking a look at the "tips on priming" and "general firewire notes" section of the guide.  it
sounds to me like the channels you can't "lock on" to are likely copy-protected with a CCI of 0x02.
It is odd, the frontend becomes unresponsive and hangs on these channels.  At times it will die when changing to these channels and then when I come back in and type in a working channel the STB will end up streaming the channel that wouldn't lock in the first place.  Last I checked the copy protection flag was empty and 5C was off, I will double check again on them later tonight though.

---

### Post by 4dognight on 2008-03-18
[QUOTE
all you should need to do is get the primer source code from the page, edit the port and node,
recompile and copy it to /usr/bin per the instructions in the guide.  part of what needs to be
handled in the future, per superm1, is configuring the correct port and node on install- since it
*is* currently hard-coded in the source.  when i get more details, this will be addressed as well.

in the meantime, thank you for your patience. ;)[/QUOTE]

So, does this mean that once it is configured, it will not change nodes on me anymore, in .21? Because in .20 it does this almost everytime I reboot. Which makes it a pain. I usually end up unplugging the 1394 cable and then reinserting to get it back on the configured node.

---

### Post by majoridiot on 2008-03-18
> **4dognight said:**
> So, does this mean that once it is configured, it will not change nodes on me anymore, in .21? Because in .20 it does this almost everytime I reboot. Which makes it a pain. I usually end up unplugging the 1394 cable and then reinserting to get it back on the configured node.

no.  

what you are describing is an issue with the stb "jumping nodes" on reboot 
and not an issue with mythtv or the primers, etc.  some boxes do this for unknown
reasons (at least to me).

a workaround you can try, which works in most cases like this:

immediately after rebooting (and node change), use firewire_tester to issue 
a bus reset (-R option) and see what node the stb is on.  do this a few times and 
see if the stb continues to jump nodes, or settles on one.  chances are, it will
settle.  next, reboot again and immediately issue a bus reset again.  check the 
node and see if it matches the node it settled on last time. chances are it will.

if this is the case, then all you need to do is use that port and node for the primer,
making sure to issue a bus reset before priming.

---

### Post by rhpot1991 on 2008-03-18
Its worth noting that MythTV now uses a GUID to identify firewire devices so it no longer needs to the ports or nodes.  But, the mythprimer still needs them.

Edit: I forgot to mention that changing the ownership of /dev/raw1394 should no longer be needed, verify that mythtv group has ownership if it while the backend is stopped.

---

