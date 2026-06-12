---
title: "[SOLVED] Wmv and avi files in Totem"
date: 2008-08-01
forum: Multimedia Software
---

### Post by azangru on 2008-08-01
This looks like a codec problem, but I can't figure out how to solve it. Whenever I try to play wmv and some of the avi files with Totem, I get only a window with shapeless horizontal smears, greenish, or bluish, or whatever other color they go. Other avi-s, play fine, as do mpeg video, youtube video, or flash video.

The VLC media player, on the other hand. plays those stubborn wmv-s and avi-s without any problem.

Now, my system is Ubuntu Hardy. I installed the restricted extras from the multiverse. What else do I need to do to make Totem play wmv-s and avi-s correctly?

---

### Post by kostkon on 2008-08-01
> **azangru said:**
> This looks like a codec problem, but I can't figure out how to solve it. Whenever I try to play wmv and some of the avi files with Totem, I get only a window with shapeless horizontal smears, greenish, or bluish, or whatever other color they go. Other avi-s, play fine, as do mpeg video, youtube video, or flash video.

The VLC media player, on the other hand. plays those stubborn wmv-s and avi-s without any problem.

Now, my system is Ubuntu Hardy. I installed the restricted extras from the multiverse. What else do I need to do to make Totem play wmv-s and avi-s correctly?
You could install the Windows codecs *w32codecs* package (or *w64codecs* if you have a 64bit Ubuntu) that is offered by the [*Medibuntu* repository]("http://www.medibuntu.org/"). Add this repository to your software sources list (instructions on how to do it are on the site) and then install the package from *Synaptic*.

Also, make sure that the *gstreamer0.10-pitfdll* package is installed.

---

### Post by azangru on 2008-08-01
> **kostkon said:**
> Also, make sure that the *gstreamer0.10-pitfdll* package is installed.

I checked. It is.

> **kostkon said:**
> You could install the Windows codecs *w32codecs* package (or *w64codecs* if you have a 64bit Ubuntu) that is offered by the [*Medibuntu* repository]("http://www.medibuntu.org/"). Add this repository to your software sources list (instructions on how to do it are on the site) and then install the package from *Synaptic*.

I did as you suggested, but it didn't help :(

---

### Post by jualin on 2008-08-01
Install these > sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-plugins-good

---

### Post by azangru on 2008-08-01
```
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

:(

---

### Post by jualin on 2008-08-01
Let me see what else could be

---

### Post by jualin on 2008-08-01
How about using xine instead of gstreamer. > sudo apt-get install totem-xine libxine1 libxine1-plugins libxine1-all-plugins libmpeg4ip-0 

---

### Post by azangru on 2008-08-02
> **jualin said:**
> How about using xine instead of gstreamer.

Erm... Can you expand a little bit on this option? Will Xine co-exist with gstreamer or remove it altogether? Is it safer to install Totem-Xine manually, like you say, or through add-remove in the applications menu? Is it easy to roll back to gstreamer if there are any troubles with xine?

Sorry for the lame questions - it's just that I am still new to Ubuntu.

---

### Post by silkstone on 2008-08-02
This is the code I use to install codecs and other applications for streaming and playback. It is taken from a tutorial on these forums. Take a look through it and see if anything is missing from your set-up. Obviously the java stuff isn't relevant, but I've included it for completeness.

sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss compizconfig-settings-manager faad **gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll** libflashsupport liblame0 sun-java6-fonts sun-java6-jre sun-java6-plugin unrar **w32codecs**

This is for 32-bit Hardy - if you're using 64-bit I have the code for that too - please ask!

EDIT/ The relevant packages are in bold.

---

### Post by azangru on 2008-08-02
By the way, I'm reading the *Customizing Ubuntu* blog that Jualin links to and found out that after installing w32codecs I can now play the Real Audio files in Totem. Nice feature!

---

### Post by azangru on 2008-08-02
> **silkstone said:**
> This is for 32-bit Hardy - if you're using 64-bit I have the code for that too - please ask!

No, no, I have the 32-bit version, thanks.

I looked up in the Synaptic Manager, aand here's what I see:

> **silkstone said:**
> **gstreamer0.10-ffmpeg**

Check

> **gstreamer0.10-plugins-bad**

Check

> **gstreamer0.10-plugins-bad-multiverse**

Check

> ** gstreamer0.10-plugins-ugly**

Check

> **gstreamer0.10-plugins-ugly-multiverse**

Check

> **gstreamer0.10-pitfdll**

Check

> **w32codecs**

Check

And yet - no luck. Weird :(

---

### Post by azangru on 2008-08-02
> **azangru said:**
> And yet - no luck. Weird :(

That's just to show you what I mean:

Totem player:

[IMG]http://farm4.static.flickr.com/3266/2724214863_7a922bbffe_o.jpg[/IMG]

Same file in VLC player:

[IMG]http://farm4.static.flickr.com/3263/2724214867_89322c6680_o.jpg[/IMG]

---

### Post by silkstone on 2008-08-02
Yes that is odd. Do you have desktop effects enabled, and if so does it make any difference if you turn them off?

There's no harm in using VLC, but totem should work and I don't know what else to suggest - sorry.

---

### Post by azangru on 2008-08-02
> **silkstone said:**
> Do you have desktop effects enabled

Nope. I have a VIA motherboard with integrated graphics; I doubt desktop effecs will even work for me.

---

### Post by silkstone on 2008-08-02
You could try totem-xine instead of totem-gstreamer.

I haven't done this, but I believe that you don't need to change the backend of Totem - just install an alternative GNOME frontend for Xine called Gxine:

sudo apt-get install gxine libxine1-ffmpeg

See this for a complete guide - it's very good.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by jualin on 2008-08-02
> **azangru said:**
> Erm... Can you expand a little bit on this option? Will Xine co-exist with gstreamer or remove it altogether? Is it safer to install Totem-Xine manually, like you say, or through add-remove in the applications menu? Is it easy to roll back to gstreamer if there are any troubles with xine?

Sorry for the lame questions - it's just that I am still new to Ubuntu.

Sorry about not explaining to much, I was in a hurry yesterday. Xine and Gstreamer are the multimedia engines commonly used in Linux (what makes media play). You can install one or another and you can even use xine for some applications and gstreamer for others. You can go and install them using Synaptic Package Manager, found in System, Administration and looking for the packages that I told you earlier. To use xine in Totem you need the package "totem-xine" and to use gstreamer you need the package "totem-gstreamer". I believe that you cannot have both totem-xine and totem-gstreamer installed at the same time, however if you want to go back and use gstreamer you can simply right click on the package "totem-xine" and select "Removal", and then just install "totem-gstreamer". Everytime you want to install or uninstall a package you would use Synaptic Package Manager. The "Add and Remove" found in applications has a shorter list of packages and sometimes the names are different than the names in Synaptic, so I suggest you to use Synaptic Package Manager. Good luck!

---

### Post by azangru on 2008-08-02
OK, I installed totem-xine through Synaptic Package Manager, and now it appears I have both the xine and gstreamer. Do I have to somehow switch Totem to make it use xine instead of gstreamer?

---

### Post by jualin on 2008-08-02
You have to remove the package totem-gstreamer via Synaptic Package manager or via terminal > sudo apt-get purge totem-gstreamer

---

### Post by azangru on 2008-08-02
Y-y-y-y-y-e-e-e-e-e-s-s-s!

Switching to Xine did the trick!

Thanks so much!

---

### Post by azangru on 2008-08-02
Ouch! Now Totem wouldn't open files within Firefox, as it used to :(

---

### Post by jualin on 2008-08-02
Glad to hear that! Just make sure you mark the thread as solved. And sorry for not explaining that much at the beginning. Greetings from Miami, FL, USA

---

### Post by azangru on 2008-08-02
> **jualin said:**
> Just make sure you mark the thread as solved.

I will. :) Just before I do that, though -- I don't know whether this belongs to this thread or whether it's a separate issue -- do you by any chance know how to integrate Totem with Firefox? So that when I click on a wmv file in Firefox Totem would fire up and play it? It used to be that way with gstreamer: Totem showed rubbish, of course, but at least it tried to play wmv-s from Firefox. Now it doesn't want to do this.

Sure, I can enter the address of the wmv in the Open Location menu of Totem, but starting up Totem with just a click on a file was so much cooler :)

---

### Post by jualin on 2008-08-02
I think that the package you need is called "totem-plugin" you can install it via Synaptic Package Manager or via terminal > sudo apt-get install totem-plugin

---

### Post by azangru on 2008-08-02
> **jualin said:**
> I think that the package you need is called "totem-plugin"

Can't see it. There are totem-plugins (which are checked in Synaptic).

There is another curious thing: Synaptic tells me there are quite a lot of gstreamer plugins left: 

[IMG]http://farm4.static.flickr.com/3161/2726090020_e1e1e2638a_o.png[/IMG]

Some of them are related to pulseaudio. Does this mean I'll have to remove all gstreamer packages?

---

### Post by jualin on 2008-08-02
You don't need to delete those plugins if you don't want. I don't know if another application in your system is using those plugins. And sorry about that I meant "totem-mozilla". I am not in my Ubuntu machine right now so I am just doing it by memory. Check if you have that one installed (totem-mozilla)

---

### Post by azangru on 2008-08-02
> **jualin said:**
> Check if you have that one installed (totem-mozilla)

Yep.

There even is a xine-plugin, and I tried to install it too, but it didn't help :(

---

### Post by jualin on 2008-08-02
Check on Firefox that you have the plugin enabled. I am not on my ubuntu machine so I dont remember how to do that but I think it was under Tools and Addons.

---

### Post by azangru on 2008-08-02
I went to Edit-Preferences in Firefox, and here's what I see:

[IMG]http://farm4.static.flickr.com/3138/2725331263_b511257c39.jpg[/IMG]

It's funny that Windows Multimedia Video files (wmv-s) ask for the Windows Media Player plugin, and not for the Totem web browser plugin. There's no straightforward way to assign the Totem plugin to this file type, too: the drop-down menu offers either Windows Media Player plugin or the standalone Movie Player. Can this be the reason why wmv's wouldn't play?

In the add-on list I have Totem web browser plugin, VLC multimedia plugin and Windows Media Player plugin.

---

### Post by jualin on 2008-08-02
I have two suggestions. The first one is install the package "xine-extracodecs" via synaptic or terminal > sudo apt-get install xine-extracodecs Then restart Firefox and check to see if it works.

My second suggestion (if the first one fails) is to use VLC Player in Firefox for the playing of WMVs in firefox. To do this you need to install the VLC Plugin for Mozilla found on the package "mozilla-plugin-vlc" or via terminal > sudo apt-get install mozilla-plugin-vlc For the second suggestion to work you need to remove totem-mozilla. Good luck!

---

### Post by azangru on 2008-08-02
> **jualin said:**
> Then restart Firefox and check to see if it works.

OK, my mistake was that I didn't restart Firefox. I re-installed totem-mozilla and xine-plugin, and now everything works.

Phew, problem solved. Thanks again!

---

### Post by jualin on 2008-08-02
No problem, glad everything is working. I will keep that in mind for next time, I'll ask "Have you restarted Firefox?", :lol: Sometimes we forget to try the simple stuff first and suggest the complicated solutions.

---

