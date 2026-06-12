---
title: "[SOLVED] Standalone vsti"
date: 2007-10-24
forum: Multimedia Production
---

### Post by Fingers &amp; Thumbs on 2007-10-24
Hello everybody.

    I want to load some vst instruments but don't need any sequencers or DAW's.

   What's the absolute minimum I need to install to get vsti's to run?

Or alternatively, what's the minimum I need to install to make it as easy as poss to run vsti's?

 Thanks in advance.

---

### Post by nalmeth on 2007-10-25
VST is tricky in Linux, because there aren't many native VST or VSTi's available. So they have to be run using WINE and a hosting application like DSSI and/or FST, and JACK. 
As a result of using WINE to run windows VST plugins, not all of them work, or work correctly.

This is a decent site where users post how well VST plugins are working:
[http://ladspavst.linuxaudio.org/](http://ladspavst.linuxaudio.org/)

Simply put, try this tutorial to setup VST: [http://ubuntuforums.org/showthread.php?t=557466](http://ubuntuforums.org/showthread.php?t=557466)
and go from there

---

### Post by Fingers &amp; Thumbs on 2007-10-25
Yay! "The Band" Good taste sir!

Thanks for your response, I'd given up trying to find good info on the subject, but I've just followed those instructions, and with a little further tweaking i now get no errors. I'm yet to try installing my favourite instruments (Akoustik Piano, The Grand, B4) as I am not at home, but I can't wait to get home and give it a shot.

  I'll report back with the results.

Thanks again.F&T

---

### Post by eric71 on 2007-10-26
An easier way, I think:

Make sure wine, qjackctl,  and dssi are installed via synaptic. Locate a .deb for and install dssi-vst (see [http://ubuntuforums.org/showpost.php?p=1310545&postcount=13](http://ubuntuforums.org/showpost.php?p=1310545&postcount=13) ). Put your vsti dll's in a folder called "vst" in your home directory. Run the command dssi-vst-scanner in a terminal. This should register all the .dll's in a file called dssi-vst.so. Then to run the vsti as a stand-alone Jack aware program, after starting jack with qjackctl just type jack-dssi-host dssi-vst.so:vstiname.dll

For instance, for the drawbar organ vsti, AZR3, I would use:

jack-dssi-host dssi-vst.so:AZR3.dll

It doesn't play nice with vsti's that have spaces in their names. When you type the command, just replace the spaces with asterisks, and it works fine.

The post where you can get dss-vst mentions using the command "vsthost", rather than "jack-dssi-host", but the Vst's always crash after a few seconds when I use it. It's a lot to type, but you can just create launchers for your favorite VSTi's.

---

