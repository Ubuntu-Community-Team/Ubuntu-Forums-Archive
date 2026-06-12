---
title: "from xp to mythbuntu"
date: 2009-10-28
forum: Mythbuntu
---

### Post by carolinamagi on 2009-10-28
Hello Mythbuntu users!

I am in search of some advice and any recommendations from the Mythbuntu community about transitioning from an Windows XP based HTPC to a Mythbuntu based HTPC,

Let me start with a brief background.

I am no new to Ubuntu and have used it for over two years. I have grown used to the operating system and have become competent in hacking my way to making the system work to my needs. I wouldn't say I am expert but I feel comfortable with Ubuntu enough to provide basic tech support for friends; or would if any of them use Ubuntu.

My HTPC is a seperate system.
Specs include:
AMD Athlon X2 Dual Core processor clocking in at 2.1Ghz
4GB of RAM
Nvidia Geforce 5200
Hauppauge WinTV PVR PCI II (52xx)
I use onboard audio

I built my system two years ago. At the time MythTV was the better (best?) option for Linux based HTPC software but I sided with Windows XP instead as MythTV had lost it's free online tv listing source.

I installed Snapstream's Beyond Media and Beyond TV and while they have served me well I am getting a bit fed up with BM. I won't bore with the details.

I am looking into dumping XP for Mythbuntu. I don't expect to run into too many issues but I would still like to know how much of a fight I'm in for to switch operating systems and HTPC frontends.

Hardware wise, I am only concerned about my Snapstream Firefly remote. It is an RF based remote. I have zero interest in purchasing any new hardware, as ridiculous as that might seem, and having to buy an IR blaster and remote will be a deal breaker.
Has anyone made the switch and made the Firefly (not firely mini) work?

Software wise, what can I expect? I have two years worth of .avi files recorded from Beyond TV.
Will these files be easily incorporated into Mythbuntu easily? Will they be sorted by TV show or will I have to monkey around to get them to organize appropriately?
How do you all like the program guide?


I know I have a lot of questions but I don't want to jump ship without looking into some of the issues involved. The HTPC in my house is mostly used by my wife and I want to make sure that the transition will be as seamless possible.

Thanks for your help!

---

### Post by blackoper on 2009-10-29
I have the snapstream firefly remote working for mythbuntu, xbmc and boxee (the rf snapstream firefly). If you'd like the necessary config files I can get those for you. It was harder to get going than I would have liked and it took an hour of searching forums to get the right working config files.

If they are just .avi files you can have those displayed with myth video plugin easily by just including them in the mythvideo directory. There is a script in the contrib section for importing files if you want them to be added to the recorded program section but I'm not sure how that will go with beyond media content.

Biggest issue will be getting used to a linux/ubuntu environment. You will probably run into some issues that will require googleing, etc. Also you are going to be tempted to upgrade to things like a hauppauge 1212 (Hdpvr) for hd recording of your cable box and adding a lot of hard drives, then you'll want a network booting atom ion board on every tv, etc. It really doesn't end. Welcome to the sickness :)

---

### Post by mrand on 2009-10-29
Howdy there,

The main mythtv wiki is invaluable for some of the things you asked about, especially hardware.  The first hit on google on that remote + mythtv is this: [http://www.mythtv.org/wiki/Snapstream_Firefly](http://www.mythtv.org/wiki/Snapstream_Firefly)

The best way to learn about Myth is to try it.  And thanks to wubi, you can do that without even having to repartition your hard drive if that makes you nervous (or you can use a different hard drive, or shrink existing partitions with gparted to make room for a test install).

As you may have read, the latest version of MythTV (0.22) is in the final throws of being released - Mythbuntu 9.10 includes a snapshot of the release candidate.  Some people run into a bug here or there, but overall it works great.  The new user interface is getting raves, and the developers aren't even done extending it!  The 0.23 release (next year) will be killer, along with tons more cool themes.  I actually haven't used the 0.22 program guide much, so I can't offer an opinion on it.

Importing and playing existing media is generally not hard.  The super easy way is simple group them by show and let MythVideo handle them.  If  the files are named in a certain format (and if they aren't, you may be able to throw an easy script to rename them), 0.22 will auto-retrieve fan-art for them.  The only down side of this is that it places the files in the "videos" listing rather than the "recordings" listing.  If you really want it in the recording listing, I believe you'd want to check out:
[http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl](http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl)
I've not used this, but it appears that it would not be hard to script up something to parse descriptive filenames and feed that as arguments to Myth.rebuilddatabase.pl.

Have fun!

[INDENT]Marc[/INDENT]

---

### Post by carolinamagi on 2009-11-03
Thanks for the responses! I am going to boot up the Live CD tonight and see how it looks, feels and works. I'll keep this post updated if anyone has interest.

Thanks again!

---

### Post by carolinamagi on 2009-11-05
well . . .
I decided to use a spare hard drive to do a full install onto my htpc. the live cd booted but i couldn't get a real feel for the interface b/c it loads into the desktop mode and things like the frontend, remote support, and even the tuner card were absent.

the install went fine. the setup did not. i've obviously been spoiled in my previous ubuntu setups because this was terrible. I could not get the remote to work, which was fine because I didn't spend too much time on it. I was willing to test the system with a keyboard and mouse. 
What really bothered me was the trouble I had with my tuner card, the Hauppauge pvr-150: no dice. It looked as if it was found and configured properly but I couldn't get an image. My attempt to sign up for the chanel guide went ok but the listings never downloaded.

To sum it up, I feel like Napoleon marching his troops into Russia. Fine idea that was horribly executed.

Because I don't have a whole lot of time to spend on this lateral shift from XP/Beyond TV to Mythbuntu I am going to shelve the project for now. I'm considering quiting the dedicated HTPC for a stand alone product, no not tivo, but maybe that new stand alone hauppauge gadget.

If and when I return to mythbuntu I'll keep you posted, no pun intended.

---

