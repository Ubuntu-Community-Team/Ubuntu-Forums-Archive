---
title: "iMON Remote 0 button not seen by LIRC"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by carlb on 2007-01-30
I am trying to set up a Soundgraph iMON Remote in Ubuntu.  The model is the iMON pad with volume control knob.  The knob/ ir receiver is connected via USB.   I have LIRC installed and can recognize all but three buttons of the iMON pad using the "irw" command.  The problem I  am having though is that the 0 (zero) button is not being recognized in Ubuntu.  The remote is transmitting.  The reason I can tell this is that the IR receiver is built into the Volume control knob.  This setup is referred to as the Soundgraph iMon Knob.  Pressing the 0 button causes the knob's blue LED to flash indicating it is reciving a signal.  This LED flashs anytime a key is pressed on the remote to indicate a signal is being received.

I also cannot see any  "irw" response from the Next Chapter button and the Thumbnail button but I could live without those two being functional.

Can anyone suggest how to further debug or fix the inability of LIRC to recognize the 0 button of the remote.  Since this is a frontend Mythtv machine, having the 0 button work is critical.  I can change channels in Mythtv through the remote, but obviously can't tune a channel that has a zero number.  And my wife says this is unacceptable because the Food Channel is on channel 60!

Thanks in advance for any suggestions.

---

### Post by GG_HTPC on 2007-07-13
Did you try typing mode2 in the lirc/bin directory? irw simply publishes the name of the button pressed if the hex code is not recognized by the remote, it will not do anything.

When you are in mode2 and press the buttons, you will see the hex codes of the buttons. I had to add some hex codes manually in the lirc.conf file downloaded from the LIRC website for imon pad. Once the codes are set, it should work.

---

### Post by carlb on 2007-07-17
Thanks for the suggestion.  For the time being I put the remote on the shelf  and like many others  switched over to a wireless keyboard instead.

---

