---
title: "VSTis and Rosegarden The Easy Way"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by slaveofone on 2007-10-26
How 2 Get VSTis working with Rosegarden

Ubuntu 7.04.  I compiled nothing.  No Dssi-Vst.  No Fst.  Everything except SAVIHost and assorted VSTis can be downloaded and installed with Synaptic directly from Ubuntu repositories.

Must-haves:
JACK, WINE, Rosegarden, Aconnect, SAVIHost, assorted VSTis

Setup:
1. Assign a SAVIHost.exe to your VSTi .dlls.
2. Start JACK, start Rosegarden, then start SAVIHost with WINE for whatever VSTi you want to use.
3. In Rosegarden, set MIDI Output System Device to MIDI Through (or alternatively go into JACK's Connections and connect MIDI Output System Device to MIDI Through).
4. Place a MIDI sequence in Rosegarden.  Make sure that track is set to MIDI Output System Device.
5. Open Aconnect, drag a &#8220;wire&#8221; from the MIDI Output System Device to the MIDI Through input.
6. In your SAVIHost VSTi, go to Devices -> MIDI and change input to MIDI Through.  (I don't know what you might use, but to hear what I was playing, I needed to set Devices -> MIDI output to Emu10k1 wavetable.  What works is what you can hear.)

The Magic:

1. Select whatever patch/instrument/noise you want in your VSTi.  (Note: Because it might mess the audio if your SAVIHost VSTi is not front and center when it's being triggered, be prepared to quickly switch from Rosegarden to your SAVIHost VSTi with Alt + Tab.  You may want to give yourself a couple measures of play time before the MIDI begins so you can guarantee yourself the time you need to be looking at your VSTi and making sure it's on the patch/instrument/noise you selected before it starts being triggered).
2. Press play in Rosegarden.
3. Alt + Tab over to your SAVIHost VSTi.
4. If the patch/instrument/noise you selected changes, you've given yourself enough time to reselect it, right?  If nothing changes...
5. Sit back and don't touch anything.

Congratulations, you've got your VSTi controlled and played by Rosegarden!

While you're at it, why not record your Rosegarden-VST performance?  You can do it in Rosegarden, Audacity, or even in SAVIHost itself.

(Figure out a better way?  A better connection?  A different workaround?  Post it.)

Trouble-shoot:

Sometimes your VSTi wants to play a different patch/instrument/noise when the MIDI sequence begins or during play.  One workaround is simply to begin with Step 2 and don't select your patch/instrument/noise until Step 4 (giving yourself some blank space between the start of your MIDI sequence and some more before actual MIDI triggers).

No sound coming out of the VSTi?  Unable to make the appropriate connections in Aconnect?  Make sure that WINE's Audio is set to ALSA in winecfg.

---

