---
title: "How to successfully connect my Nintendo DS to wifi card in master mode?"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by wakkawakka on 2010-12-03
Hello all!  

Technically, I'm running Linux Mint 10 and not Ubuntu.  But as Linux Mint is based off of Ubuntu, I imagine the procedure for what I'm trying to do will be the same.  

I just didn't want to post on the Mint forum because this one is much larger/more vibrant, and I figure the odds of getting help with a difficult question are much better here. 

I have a Linksys WPC11 ver.3 wifi card that I want to use as an access point, through which I intend to connect my Nintendo DS for multiplayer gaming.  

I know I can get a wireless router for next to nothing, but money isn't the issue here...Suffice it to say that I'm aware I can use a wireless router and that's not what I'm going for.  

I haven't found any guide for making a DS connect through a wifi card in master mode, just references to people having done it.  

So I spent virtually all day yesterday pouring over guides for how to do SIMILAR things, and being as though there seems to be more than one way to skin this cat (from what I've read), and given that instructions can vary by distribution, it has been extremely difficult to tease out the knowledge I'm looking for as the total Linux noob that I am.  

So first of all, I have verified that the wifi card I'm using works in master mode.  

And I am able to set it to master mode WITHOUT first installing the hostap packages, so I'm assuming that they're not needed? (I could be wrong about that, maybe they're needed for additional configuration beyond setting it in master mode?)

After putting it into master mode I was able to assign it an SSID, and verified that it was in master mode both by typing iwconfig wlan0 and checking the output, as well as making sure that the hotspot was visible to other computers (it is).

Now comes the trickier part: getting wlan0 to route traffic through eth0 so that my DS can connect to the internet.  

From what I read, it seemed that bridging the connections was the way to do this.  

So I went to a command line and performed the commands that were supposed to create the bridge, which were something like:

brctl addbr br0
brctl addif eth0 br0
brctl addif wlan0 br0

and then

brctl show

To verify that the connections were both part of br0, and they appeared to be.  

However, bridging the connections simply killed my connection.  And whatever guide I was using (and subsequent googling) didn't reveal how to create a bridge and be able to access the internet.  

Since that wasn't working, I did a little more research and found people saying that one of the easiest ways to bridge connections in Linux was to use Firestarter to set up internet connection sharing.   

So I tried that next.  However, for some reason, when I try to set up internet connection sharing through Firestarter's wizard, it always fails with the error "wlan0 not ready."  
I researched the error and wasn't able to resolve whatever was causing it, so I gave up on Firestarter.  

I read of what appears to be a *different *way of doing this, by using iptables commands and doing some other stuff to forward traffic from wlan0 to eth0...

...And on that attempt, I was totally devoid of knowledge of what each command I was typing was supposed to do, and I was basically just copying and pasting in to a terminal.

Everything seemed to be going fine until I got to a particular command (forgetting what it was now and don't have the site bookmarked on this computer), and it kept returning "blah blah blah permission denied".

This was even when I'd input "sudo" (rest of the command).  

And that kinda brings me to where I am now.  Totally lost.   

Has anyone out there done this themselves?  How did you make it work? 

I don't have to be able to surf on the net (or do anything else at all) while my DS is connected to my laptop.  I don't need ANY security whatsoever, no firewall, nothing.  I'm also pretty sure that I don't need DHCP for my DS, as I've gotten it to work just fine before with other wireless routers by assigning it an IP manually.   

Heck, the settings that allow all this to work don't even need to be persistent (unless it takes like 20 minutes to set up).

Whatever the bare minimum is that would make this work is plenty sufficient.    

Normally when I post to a forum, there's one particular step I'm having trouble with, out of an overall process that I basically understand.  

That just isn't the case here.  

So if anyone can help, please, please do.  

Thanks in advance!

---

