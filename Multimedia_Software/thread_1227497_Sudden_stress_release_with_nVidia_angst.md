---
title: "Sudden stress release with nVidia angst"
date: 2009-07-30
forum: Multimedia Software
---

### Post by jwhiz on 2009-07-30
Hi;
there are a lot of posts about tweaking config files for nVidia drivers (proprietary and open source).
After trying to get either the prop. driver or the glx-legacy driver to get me a decent screen size and refresh rate on an **nVidia GeForce2 MX-400 card** and a *Hewlett-Packard Ultra VGA 1280 monitor*, I finally looked up the monitor specs, and discovered that the Max. resolution was 1024x768@60 Hz...wait a minute, the max is the same as the only option appearing in screen res dialog?!...oh wait, isn't refresh rate sometimes tied to screen size? Hmmmmmm....I had already seen an improvement when I plugged in this monitor, replacing an even older NEC (20 years old, and made in the U.S.!)
Oddly, the monitor change was not detected until I rebooted a few times, the last time after a set of system updates. At that point, I was given a dialog during the boot which told me that the system was running at a really low res (really) and gave me the option to manually configure monitor (not the card - the monitor!) Then I was given a dialog that looked a lot like Windows hardware dialogs, which let me choose manufacturer and model. I hadn't noted yet which card I had, but there another tab which allowed me to choose nVdia Geforce options. Boot continued. I now had the open source driver enabled, but still not happy. Installed nvidia-glx-legacy from Synaptic, then rebooted. Better, but...
Went back to dialog box (under Preference/Screen Resolution), with glx-legacy driver installed and proprietary driver disabled, found screen size had defaulted to 1280x1024 (!!), with only 60 Hz available - but there was a full set of resolutions available in the drop down menu...setting this up for an older user, so chose 1024x768 (gee, like the supposed max. setting provided by the manufacturer), and then had choice of 60, 70 and 75 Hz. Chose 75 Hz (had to apply size first, then refresh rate, then close), now have decent size screen and flicker is no longer bugging me.
Did NOT end up in console, or even a terminal window, edited no files...these are sometimes fun too, but wonder if others might find they've overlooked an easy solution to the Display Disappointment right on the desktop, before plunging into the non-GUI kernel-changing learning curve. Also I don't see that many people were looking for solutions from monitor side, rather than card.

---

