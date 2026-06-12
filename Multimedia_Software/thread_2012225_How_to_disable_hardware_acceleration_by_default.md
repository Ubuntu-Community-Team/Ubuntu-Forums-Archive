---
title: "How to disable hardware acceleration by default"
date: 2012-06-28
forum: Multimedia Software
---

### Post by Oldhacker on 2012-06-28
Using 64 bit 12.04, when I enter YouTube many clips have their colors reversed UNTIL I switch to full screen and disable hardware aceleration. That only holds for the current session. The next time that I boot up, I have to go through the same routine.
Isn't there a way to disable hardware acceleration by default so that the setting becomes permanent?

Thanks

---

### Post by Oldhacker on 2012-07-08
There must be a doppelganger at work in my house.
Although no one has responded to my post about needing to disable Hardware Acceleration each time in order to view YouTube videos without reversed colors -- as of today it is working correctly without any input on my part!

Confess, Nvidia or Ubuntu. Which one of you solved the problem from afar by remote control?

---

### Post by Sylslay on 2012-07-08
Try this: 
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

PS. I test fiew "How to improve falsh"

but this above is simple and works on 64 bits system.

You can chose between repo and adobe source as well a stable and beta version

Happy testing.

:-)

---

### Post by Oldhacker on 2012-07-10
The mystery deepens further. After one day of the reversed colours on YouTube curing itself, the problem returned today - with a vengance.

I had to pull up two clips, switch to full screen, and disable hardware acceleration in each, exit YouTube and enter it again before the reversed colours would go away. I am absolutely baffled.

---

### Post by efflandt on 2012-07-10
I wonder if anyone has figured out why it is "only" YouTube videos that smurf people with reversed red/blue, when even ads on YouTube are fine, as are all other flash videos I have ever viewed anywhere.  What does YouTube do differently for their videos than anybody else?

---

### Post by SeijiSensei on 2012-07-10
YouTube uses a technology called "[stage video]("http://www.adobe.com/devnet/flashplayer/stagevideo.html")" in Flash which is the source of the problem.  Most sites don't use this feature, but YT does.

That said, I don't have the problem Oldhacker does at all.  I turned off hardware acceleration once, and it has stayed off ever since.  I'm on Kubuntu 12.04 with Firefox 13.0.1 and Flash 11.2 r202.  Both of those are the current versions from the repositories, though for Flash I have the Ubuntu "partner" repository enabled and got the Flash plugin from there with "sudo apt-get install adobe-flashplugin".

---

### Post by Oldhacker on 2012-07-11
Seiji-sensei,

We are using the same versions of Flash and of Firefox. The only difference that I can see besides your using Kubuntu 12.04 (which should be functionally the same as Ubuntu 12.04 except for the desktop interface) is your Ubuntu "partner" repository enabled. Where do I find this repository?

Arigato

---

### Post by SeijiSensei on 2012-07-11
If you're using a graphical package manager, edit the "Software Sources" and in the "Other Software" tab check the box for "Canonical Partners."  You don't need the source repository.

If you'd rather just do this manually, edit (as root with sudo) the file /etc/apt/sources.list and remove the hash mark ("#") from the front of the line that reads:

```
deb http://archive.canonical.com/ubuntu precise partner
```

Now run:

```

sudo apt-get update
sudo apt-get install adobe-flashplugin

```

I believe it will remove any extraneous packages like "flashplugin-installer" in the process of installing the adobe-flashplugin package from the partner repository.

Another alternative is to create (as root) the file /etc/adobe/mms.cfg and put these two lines in it:

```
EnableLinuxHWVideoDecode=1
OverrideGPUValidation=true
```

There's also a patch for libvdpau1 that you can try if you're adventurous and don't mind rebuilding .debs from source.  Read [this bug report at Launchpad](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091) for details.

---

### Post by Oldhacker on 2012-07-12
I tried your last instructions and it worked for all of YESTERDAY. ;-( When I turned on the computer today, the reversed colours were back again!

I truly appreciate your help, but this behaviour of YouTube defies description. What you say about YouTube employing a different technology than other streaming video sites has to be at the root of the condition. At least I know how to make it appear normal for one day at a time.

---

### Post by Oldhacker on 2012-07-12
I found the culprit that had been eluding me.
Before turning the computer off, I had gotten into the habit of clearing data to free up cache memory, etc. for the next boot-up. However, "Offline Website Data" was checked and that apparently was where the instruction to "Enable Hardware Acceleration" was kept. I tried turning on and off the computer with and without the "Offline Website Data" and without it checked my settings were retained. :D

Thanks again

---

### Post by firekage on 2012-07-12
> **SeijiSensei said:**
> YouTube uses a technology called "[stage video]("http://www.adobe.com/devnet/flashplayer/stagevideo.html")" in Flash which is the source of the problem.  Most sites don't use this feature, but YT does.

That said, I don't have the problem Oldhacker does at all. ** I turned off hardware acceleration once, and it has stayed off ever since.  I'm on Kubuntu 12.04 with Firefox 13.0.1 and Flash 11.2 r202.  **Both of those are the current versions from the repositories, though for Flash I have the Ubuntu "partner" repository enabled and got the Flash plugin from there with "sudo apt-get install adobe-flashplugin".

You did it with mms.cfg at /etc/adobe or did you turn it off when clicking at played movie? The other way sometimes doesen't work cause flash plugins causes to crash.

---

### Post by Oldhacker on 2012-07-12
I turned it of by clicking at played movie (that only works when one is in full screen mode.)

---

### Post by SeijiSensei on 2012-07-13
> **Oldhacker said:**
> I turned it of by clicking at played movie (that only works when one is in full screen mode.)

Me, too, firekage.  I only suggested using mms.cfg as an alternative. 

Oldhacker, that's a really strange "feature," but I'm glad you figured out what the problem was.  I was starting to grasp at straws like permissions issues in the .mozilla or .adobe directories or something like that.  I'm not sure I see how "Offline Website Data" applies to hardware acceleration!  Good to know in case we encounter this problem again.

The only thing I clear is my cache, and then only when I'm having problems with a site, especially one I'm developing! :D

---

