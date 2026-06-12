---
title: "AMD/ATI Video Card Resolution Issues to HDTV over VGA"
date: 2011-01-21
forum: Multimedia Software
---

### Post by mcd356 on 2011-01-21
Hello All,
So for a little background, I used to have this working:
AMD/ATI HD2600XT video card connected through VGA to a Samsung 1080p TV (open source drivers that came installed by default) on Kubuntu 9.04, 9.10, and 10.04 (it worked for 2 years without issues and automatically detected 1920x1080 as soon as I installed it, I never even had to mess with settings to get the right resolution).
I can't use HDMI as the HDMI tuner on my TV has been acting up (confirmed with a stand alone blu-ray player) so that is not an option.

I upgraded the video card to an AMD/ATI 5570. The results of using the same hardware and connectors on
Ubuntu 10.10:
Open source drivers only allow for screen sizes up to 1600x1200. I tried using xrandr command line to manually create a new mode and then set it. Everything works fine up to the set command, where it tells me the max screen size is 1600x1600, and refuses to set the 1920x1080. Even at a resolution of 1600x1200, I get screen flickering.
Installing the fglrx drivers through the restricted driver manager results in an invalid signal to my TV after ubuntu starts (TV shows "Mode Not Supported") and I get a black screen. I can switch to a terminal and run commands, so I know ubuntu is up and running, just an error with signal settings.

Kubuntu 10.10:
Open source drivers same as above, can only get to 1600x1200, manually trying xrandr command lines to add a new mode fails for the same reason.
Installing the fglrx drivers seems to work, I can change resolutions after reboot, fglrxinfo reports the ATI driver, but I can't set to 1920x1080 through GUI interfaces (both KDE Sys settings and ATI Catalyst), I only get up to 1600x1200. What's interesting is that if I go into the Catalyst control center and check the info for Analog screen 1 (my TV) it reports a max resolution of 1920x1080, so it looks like its getting the right EDID data from the TV, just ignoring it when it comes up with available resolutions.

Any thoughts on getting this to work on the new card, I'd really hate to think I just wasted all that money on a new video card...

---

### Post by BicyclerBoy on 2011-01-21
Are you sure that you were using VGA with the old card & working 1080 ?
Most (almost all) HDTVs will not support 1080 or any native over VGA.
They will not do VGA 50Hz modes (US does not matter) & normally they support the std video modes only.

Are you sure the hdmi is not faulty on the ext player ? More to go wrong here due to HDCP negotiation.

Maybe the ATI driver creates a pool of all modes from EDID (inc HDMI) & then will not allow them to be selected in the drop-down box ?

---

### Post by mcd356 on 2011-01-21
I'm sure that the resolution was 1920x1080 (confirmed via kubuntu settings multiple times). Although this isn't very scientific, just by walking up to the tv (46", so the individual pixels are clearly visible) I really can't think of any other resolution setting that had no distortion from stretching to fit the screen, as well as getting that individual pixel resolution, confirming that the resolution was the 1920x1080 the settings claimed it was. Finally, 2 years of seeing videos on VLC start at a 1:1 zoom clearly indicated the resolution was 1920x1080 (i.e. 720x480 videos didn't even take up 1/4 of the screen area).

EDIT: Also, I don't know if this matters, but the exact connection was DVI port on the card to a DVI to VGA adapter, then VGA cable from there to TV. My apologies on not mentioning this earlier.

As for the HDMI, I thought it might be the player for a while, but after switching around between the two HDMI inputs (HDMI1 and HDMI2) where I saw clear differences in signal issues, it only seems to make sense that there's something up with the tuner. I did try using an HDMI cable once to connect this system (after all my VGA trials failed). It kind of worked. I could see the background after boot up on ubuntu, but the size was way off (I could only see ~ the middle 1/4, maybe less of the screen, about 1000x500 px at most). I could alt+f2 to open terminal, which ended up huge (fitting my guess that it was just zooming in on the center of the desktop). I couldn't pan around to get to menus. After I switched inputs and tried to go back, I got a no signal message again (courtesy of my damaged hdmi tuner on the tv).

---

### Post by BicyclerBoy on 2011-01-21
Sure it was not DVI-HDMI single link adapter cable ?

If TV VGA input was allowing HD1080 then it must be an older model.
I'm surprised it has EDID over VGA.

Set the TV HDMI input to PC input mode maybe..
Normally direct pixel mapping is a digital link only function.

I can not believe both HDMI inputs are sick, Samsung isn't LG.

---

### Post by mcd356 on 2011-01-21
>> Sure it was not DVI-HDMI single link adapter cable ?
It's definitely a VGA cable. I remember buying it, and looking at the pins now there is no way its a DVI cable.

>> If TV VGA input was allowing HD1080 then it must be an older model.
Definitely. This TV is almost 4 years old, right around the time HDMI was starting to get integrated, where the common way to connect to projectors/TVs was still almost exclusively VGA.

>> I'm surprised it has EDID over VGA.
Maybe it doesn't. I've been giving myself a crash course on these topics to try to troubleshoot so I may be wrong on that, but it just seemed like it was since the Catalyst Control Center on Ubuntu reported the TV as an analog 1920x1080 display.

>>Set the TV HDMI input to PC input mode maybe..
The HDMI inputs basically don't have any kind of useful options. The only one for the HDMI inputs is change name... 

Normally direct pixel mapping is a digital link only function.

>> I can not believe both HDMI inputs are sick, Samsung isn't LG.
HDMI 1 (sometimes I can get it to work, usually multiple restarts of equipment and input switching is required) is worse than HDMI 2 (if I start on the antennae input and turn on  the blu ray player the connection will work, if I do that on any other input including HDMI 2, it won't, and I'll get the weak or no signal error).
I think its due to the fact that HDMI was in its infancy when I bought the TV, so I wouldn't be very surprised if the implementation was very poor. The Blu ray player is fairly new (< 1 year though, so I think its fine).

---

### Post by BicyclerBoy on 2011-01-21
The video card HDMI does not need all the HDCP handshaking/negotiation stuff to work..

Some TVs require the input name to be a certain literal "string" to do real PC mode.

Google your TV for info.

Turn off EDID mode validation for this display in xorg.conf & set up mode HD1080.
If this was nvidia X server I could provide an example.

Study your
/var/log/Xorg.0.log
for details about EDID & mode validating..

---

