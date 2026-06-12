---
title: "ati or nvidia for ut3"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by coldguy on 2007-10-22
I put together an Athlon 64X2+4600 cpu, 2GB 800MHz DDR2, 320 GB SATA, and a Gigabyte mobo w/690G chipset, integrated ATI Radeon eXpress 1250 gfx, because I'd planned on waiting till UT3 is out before getting a video card.

So which cards work better in Ubuntu, ATI or Nvidia?

I'm running Gutsy 7.10 and have enabled ATI accelerated graphics driver in restricted drivers manager. I installed the linux version of UT2004 and its running slow with medium-low settings. That seems wrong because it runs really good on high settings on my Win XP laptop with much older hardware(PentiumM, mobility Radeon 9700, 512 MB ram). I installed wine and steam, source engine games don't work at all, steam sees only DirectX version 6.14? I thought wine was up to DX9 now. I started searching forums and am confused about driver issues, but it seems Nvidia has better drivers?

I don't know if I did it wrong, but it seems integrated radeon X1250 should be faster than integrated radeon 9700, especially considering the dual core cpu and 4X the ram.  I'm going to try installing Gutsy, UT2004, wine and steam on the laptop(spare HD) to see if I get better results.

---

### Post by disturbed1 on 2007-10-22
The version of FGLRX included in Gusty is not that good***[size=10].***[/size] Though ATI does have a newer driver available, it has some issues, there is also yet an even newer than that driver due out *sometime* this month, which is taunted as including some new features, fixes, and performance increases. Although that is exactly the same press ATI/AMD have stated about the FGLRX drivers for nearly 2 years now. The issue with Wine and games is directly related to the ATI/AMD FGLRX driver.

In short, at this present time, ATI video cards just are not a serious option for games under Linux. Under Linux, an nVidia FX5500 outshines an ATI/AMD x1600 PRO. One year ago I paid $179 for the x1600, and $39 for the FX5500.

nVidia is not without fault though ;). There is a known bug when running compiz and the nVidia driver. You have a very high chance of getting the *Black Window Bug*. Which is after so many windows are open, any new window that opens results in a black window. This has to do with the available RAM of the graphics card. Also performance isn't on par with the Windows drivers using the 8600 series of cards.

I currently run a 7600GT with 256mb, and rarely experience the black window bug, but it does happen. To fix, just close a few windows. I hit the threshold with **a lot** and I do mean **a lot** of open programs.

Call of Duty 2 absolutely would not launch under wine using my ATI x1600 and the newest FGLRX nor the Gusty provided FGLRX drivers. It (COD2) works just fine using either the FX5500 or 7600GT.

I used the Restricted Drivers Manager to install the nVidia driver, and never touched my xorg.conf, no issues, and performance is just fine for what I've tried it with.

---

### Post by coldguy on 2007-10-22
Thanks for the info. Now more questions.

Is the driver enabled in the Restricted Drivers Manager the same as the ATI driver from their website that you have to do the convoluded terminal installation?

How can I tell which version fglrx I'm using?

When I run glxgrears it reports 900fps in the small window, about 110fps if I maximize it. Is that good, bad, what? 

Is there another way to benchmark the 3d performance?

What is compiz? I think I tried to enable desktop effects and it was unable.

Thanks for the info. I'm becoming less a noob all the time.

---

### Post by disturbed1 on 2007-10-22
To find the driver your using, look in synaptic. Currently for Gusty it is 8.37.6. AMD is getting ready to release 8.42.4. Ubuntu takes which ever working driver is available at the time, and packages it for easy installation. The drivers from AMD/ATI are generic, hope it works, installations. The next ATI driver, *promises*, to be great. It very well could be, but no one knows just yet. There is a web site that had beta tested the newest 8.42.4 driver, and gave it good results, but listening to that guy about ATI cards is like listening to Balmer on how great Vista is ;).

It can be painful to install the drivers from ATI's website, the same has been said about nVidia. But there is a great Ubuntu howto that works without issues for me. Though I didn't upgrade from a previous install of the FGLRX driver, it was on a fresh Gusty installation.

GLXGears **_IS NOT_** a benchmark of anything in anyway what so ever. The best benchmark is to actually play a game, and have it display the frame rate in game. There is also Umark for Linux (google it ;) ).

Compiz is the snazzy little 3d effects, like fades, transparencies, wobbly windows, and so on. YouTube has tons of videos on this.

If you already have a decent ATI card now, it's worth the wait to see what AMD/ATI does. No reason to spend more money on nVidia just yet if you've recently spent some cash on an ATI card. If you're in the market for a card anyways, it's honestly a no brainer at this point in time not to choose nVidia. nVidia's Linux drivers have consintantly been higher quality, and they, nVidia as a whole, seem to care more about the Linux community. They also have a support forum where people from nVidia actually do post and attempt to solve problems.

A shame really, because, in my ***opinion*** I believe ATI has better hardware than nVidia, ATI/AMD just can't write drivers to save their lives. It's the same situation for Window's ATI drivers. Though not in the same sad shape as the Linux counter part, they too leave a bit to be desired. nVidia's hardware seems to be a notch below ATI's, not much, just a notch. But this notch is jumped over, and made up by a large margin because of, much higher quality drivers.

---

### Post by happycampers on 2007-10-22
The 8.42.x drivers should help considerably.  I have an X1400 and the 8.41 driver increased my 3Dperformance by almost 70%, though I had to revert because of 2D issues (8.41 is not recommended for X1000, X100, or 9000 series chips).  As far as your X1250 vs the 9700, I think you'll be very disappointed if you expect the X1250 to surpass or even equal the 9700. The 9700 was the top-of-the-line offering when it came out, with lots of dedicated memory and more pixel pipelines than the lesser offerings.  The X1250 is the successor to the 9200.  While it has support for more recent DirectX revisions (at least 9.0c under Windows), it was really not meant to be a gaming card.  If memory serves, the 1250 is an SMA (shared memory) chipset, with no dedicated RAM.  That will hurt 3D performance a lot.  Older games should play okay, but I doubt you'll ever get anything much more recent than Quake3 to give decent framerates.

---

