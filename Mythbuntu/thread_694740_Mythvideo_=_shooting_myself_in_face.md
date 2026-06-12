---
title: "Mythvideo = shooting myself in face"
date: 2008-02-12
forum: Mythbuntu
---

### Post by RFinn on 2008-02-12
I've posted on this a few times, but I still haven't found a solution so here it goes again. 

I'm trying to use Mythvideo to watch downloaded movies but every player I try has a different problem. 

If I set the player to internal or mplayer it plays standard (non-widescreen) videos fine, but anything widescreen gets squished to fit full screen on my 27" CRT TV. Command line changes in Myth setup do nothing, and I can't toggle the aspect ratio. Strangely when I switch from the TV to my 19" LCD monitor everything plays fine (can't afford widescreen TV right now or i'd buy one to fix the problem). I tired enabling the XV overlay in xorg.conf and this let me switch the aspect ratio ok, but I ended up with the opposite problem where non-widescreen videos would play letterboxed and stretched.

If I switch to Xine I get absolutely no aspect ratio problems, but certain videos won't work. I assume it's a codec problem with Xvid or another codec but I can't find any info on how to update the codecs or fix the problem.

If I switch to VLC, it plays all of my videos and the aspect ratio is fine. However, I have absolutely no remote support (PVR-150 Windows remote with mce_usb2 drivers enabled) and haven't found any info on how to enable it.   

Sorry this is such a laundry list of problems, but if anyone has an idea on how to get even one of these players working fully that would be awesome. I mostly want to fix the aspect ratio for the internal player as it's smoother than Xine or VLC.

OK, thanks.

---

### Post by newlinux on 2008-02-12
There are a lot of things to try, such as using different resolutions and making sure you have the aspect ratio setup properly in mythfrontend. But if you have posted this many times, then I'm guessing you've tried most of these things. how is your computer connected to your TV (VGA, s-Video ,component)? What video card do you have and do you have propietary drivers installed. If Nvidia, have you played around with nvidia-settings? What happens when using the internal player when you cycle through the aspect ratios (w key)? Does it work when you watch recordings from your PVR-150?

When you say your PVR-150 remote doesn't support VLC what do you mean? VLC supports LIRC. Is it that you don't know what VLC's LIRC commands are? You can get a list by doing:

```

vlc --help --advanced | grep key

```

And set it up buttons in your ~/.lircrc file like:

```

begin
 prog = vlc
 button = play
 config = key-play-pause
end

```

---

### Post by theacoustician on 2008-02-12
Path of least resistance for you sounds to be to fix Xine.  Did you install the restricted codecs yet?

As for the other things you mention, switching from composite/svideo on the TV to VGA/DVI on a monitor could be a whole laundry list of issues.  I would suggest sticking with one display or the other and working all the troubleshooting measures you can before switching to the other.  xorg conf. issues could be the problem.  Bad encodes or improperly set SAR or DAR flags seem likely too if you're grabbing torrents from all parts of the internet.

In addition to what newlinux already said, it might be helpful to know your system specs and the types (resolution, codec) of videos you're trying to watch.

---

### Post by david.birch on 2008-02-12
Hi,
  if your using mplayer, you can add these lines to your .mplayer/input.conf file (create it if need be)

F1 switch_ratio 1.3333
F2 switch_ratio 1.7777
F3 switch_ratio 1.85
F4 switch_ratio 2.3
F5 switch_ratio 0

now you can switch aspect ratios if needed in mplayer with the function keys listed.

i have a line
monitoraspect=16:9

in my .mplayer/config file as most content i play is 16:9, then switch using the function keys as needed.

cheers

---

