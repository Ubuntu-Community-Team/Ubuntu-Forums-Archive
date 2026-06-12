---
title: "Black screen on NVIDIA 6200 (VGA connection)"
date: 2011-09-17
forum: Mythbuntu
---

### Post by the_dark_light on 2011-09-17
The machine I'm currently testing mythbuntu on has a Geforce 6200 graphics card (VGA and DVI output)

I intend to connect to my television (Sony Bravia - reported as DFP-0 in NVIDIA X-Server settings) by VGA.  I opted for VGA as I ran in to issues with DVI.  I found that I could connect to the televisions HDMI input using a DVI/HDMI adapter but there are serious overscan issues.  Googling this issue I found that it can be solved but does not appear to be a trivial fix.

VGA worked okay when I first set up the NVIDIA driver but now I've found that I get a black screen.  At this point I can't connect via VNC so would I be right in thinking that the X server is not running?  From what I've read I think the issue is to do with attempting to output on DVI?

I ran in to this issue with Nouveau as well, as a result I could only resolve the issue by uninstalling nouveau and using the standard VGA driver.  This resolves the issue but output resolution is limited and the lack of acceleration causes poor performance when watching video (live tv used to test)

The HTPC I plan to install on when replacing my current windows media center is an MSI K9N6PGM2-V with integrated NVIDIA MCP61P graphics (Chipset is nForce 430).  This only has a VGA output (no DVI/HDMI etc).

My question is: Is this board likely to suffer from this issue? :confused:

I would test on that machine directly but it's running as an HTPC and has many scheduled recordings.  Other family members would not take kindly to that :(

If the onboard graphics will behave okay then I can live with the overscan issues for now (I do most of my testing/configuration through SSH and VNC anyway and I'm planning on setting up a remote frontend to work with it anyway)

---

### Post by nickrout on 2011-09-17
fixing sony bravia overscan is trivial:
> 
On the Bravia I selected HOME > Settings > Setup > Screen Settings > Display Area

It was set to NORMAL
I changed it to FULL PIXEL

(from the first page on a google search)

Use the nvidia drivers, not nouveau.

---

### Post by the_dark_light on 2011-09-18
> **nickrout said:**
> fixing sony bravia overscan is trivial:


(from the first page on a google search)

Use the nvidia drivers, not nouveau.

Ah, Ii was trying to resolve it on the PC and rather than the TV end.   The process I found was a long winded trial and error approach.

Thanks

---

### Post by nickrout on 2011-09-18
> **the_dark_light said:**
> Ah, Ii was trying to resolve it on the PC and rather than the TV end.   The process I found was a long winded trial and error approach.

Thanks

Why? The problem is at the TV end and very easy to fix.

---

