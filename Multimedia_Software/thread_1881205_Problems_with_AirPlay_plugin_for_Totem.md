---
title: "Problems with AirPlay plugin for Totem"
date: 2011-11-15
forum: Multimedia Software
---

### Post by javierfh on 2011-11-15
Hi ,

I have followed this tutorial ([http://www.omgubuntu.co.uk/2011/01/airplay-video-playback-comes-to-totem/]("http://www.omgubuntu.co.uk/2011/01/airplay-video-playback-comes-to-totem/") ), to try to stream video from my Ipad to my Ubuntu 11.10, but no luck.
Everything goes just fine, until the step of enabling the AirPlay plugin from within totem, the plugin wont even appear in the list.
Has anyone got that working? where are the totem plugins stored? Im asking that one because i had to create some extra folders for plugins in totem, but i wonder where are all the other plugins, maybe i should add the files there.

I would appreciate any help you can provide. At this point, this is more a Totem issue than the airplay itself, havent got to that point yet.

Thanks in advance,

Javier

---

### Post by tyce on 2011-11-15
I'm having the same problem.  I've tried placing the files in both:

~/.local/share/totem/plugins
/usr/lib/totem/plugins

Either way, the plugin does not appear in the list when I relaunch totem.

Thanks in advance.

---

### Post by javierfh on 2011-11-15
In fact, I just installed the Arte pluging (even if I don't needed, you can find it from the software center) just to see if it appears in the list and yes it does, but also to try to find where the files get installed, but no idea. I cant find them anywhere.

So I am wondering, where are located the rest of the totem plugins, that appear in the list?, or from where that list is populated?

Has anyone succeeded installing that plugin? and was that in ubuntu 11.10? Im wondering if that might have anything to do, meaning that the totem version is different.

Lets see if we can get this solved, would be really cool.

Javier

---

### Post by Arathon on 2011-11-16
Having a similar problem. As tyce suggests, I've tried both the user local (.local/share/totem/plugins) directory and the system-wide (/usr/lib/totem/plugins) directory. Neither seems to work.

I have also tried to follow the pattern (found in the existing plugin files within the system-wide directory) of using .plugin instead of .totem-plugin as the extension for the airplay plugin.  I've tried this with both a symlink from one name to the other and renaming. Neither works.

---

### Post by javierfh on 2011-11-16
Was that working for you in 11.04? 
Can that be something related to 11.10? When the post containing the instructions was released, people reported it was working, but that was around 9 months ago, so wondering if something has changed.

I tried also with airfoil (even if is only for music [http://rogueamoeba.com/airfoil/speakers.php](http://rogueamoeba.com/airfoil/speakers.php)) but didnt work either. I dont know what can be wrong, but wish we could fix that.

---

### Post by javierfh on 2011-11-16
Damn it, I can confirm it, at least in ubuntu 10.10 it is working, just installed it at work and works perfectly, at least the part where the plugin will appear in the list. I dont have the ipad here, but i will try to test it. 
It seems that this is definetively something to do with the newer ubuntu or totem or both...or maybe the plugin files. Hmmm this is frustrating.

---

### Post by Arathon on 2011-11-16
I'm not surprised to hear that, but I had never tried it before 11.10.  

More than likely, it was yet another casualty of the poor development process that was 11.10.

---

### Post by dkados on 2011-11-22
For me it was working with 11.04. As of 11.10, when starting totem  the following error is thrown
totem --debug
(totem:22916): libpeas-WARNING **: Could not find 'Module' in '/home/kados/.local/share/totem/plugins/airplay/airplay.plugin'

(totem:22916): libpeas-WARNING **: Error loading '/home/kados/.local/share/totem/plugins/airplay/airplay.plugin'




Seems, that totem has a problem with python plugins....

---

### Post by TheMunch8 on 2011-11-28
Has anybody been able to figure out how this can be fixed? I have been poking around in the files but do not seem to be getting anywhere 

There are other working totem plugins that use Python.

---

### Post by TheMunch8 on 2011-11-28
I have made some headway....
in airplay.plugin I changed the header from [Totem Plugin] to [Plugin].  It is now showing up in Totem's Plugin list...but the following error pops up when I enable it.\:


/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
Traceback (most recent call last):
  File "/usr/lib/totem/plugins/airplay/airplay.py", line 27, in <module>
    from AirPlayService import AirPlayService
  File "/usr/lib/totem/plugins/airplay/AirPlayService.py", line 31, in <module>
    from ZeroconfService import ZeroconfService
  File "/usr/lib/totem/plugins/airplay/ZeroconfService.py", line 23, in <module>
    import avahi
ImportError: No module named avahi

(totem:5727): libpeas-WARNING **: Error loading plugin 'airplay'

Will keep updating...

---

### Post by TheMunch8 on 2011-11-28
Just did an apt-get install python-avahi.  Now getting the following error:


totem --debug
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
Traceback (most recent call last):
  File "/usr/lib/totem/plugins/airplay/airplay.py", line 29, in <module>
    class AirPlayPlugin (totem.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

(totem:5917): libpeas-WARNING **: Error loading plugin 'airplay'

---

### Post by TheMunch8 on 2011-11-28
from this [link]("http://code.google.com/p/pagavcs/issues/detail?id=142"), figured out we need to replace: 'import gobject' with 'from gi.repository import GObject'

It got me thinking, perhaps all these imports are old... So I did a quick compare to iPlayer's plugin, and did some copying from that code...


The first actual lines of code for airplay.py are changed to this:

from gi.repository import GObject
from gi.repository import Peas
from gi.repository import Gtk
from gi.repository import Totem
#import totem
import platform
import time
from AirPlayService import AirPlayService

class AirPlayPlugin (GObject.Object, Peas.Activatable):
        __gtype_name__ = "AirPlayPlugin"

        object = GObject.property(type = GObject.Object)

        def __init__ (self):
                GObject.Object.__init__ (self)
                self.totem = None


So the plugin is actually showing up, and is able to be enabled.  Unfortunately, my iPhone is not picking up a AirPlay enabled screen yet....

Anybody get it working yet?

---

### Post by TheMunch8 on 2011-11-28
For some reason, it looks like it is not being advertised on the network...Perhaps something wrong with the ZeroConfService.py file?

---

### Post by javierfh on 2011-11-30
Hey thank you so much for the investigation and keeping the rest updated.
In fact I tried it with my work computer, where I have ubuntu 10.10 and there I could install the plugin and select it, but the Ipad can't see it.
Anyway I guess you will get further with your investigation, you seem to be following the right track.

Thanks again and I hope you can get it fixed, would be so cool.

---

### Post by TheMunch8 on 2011-12-01
So, I made another discovery.  

It looks like Totem changed the way that python plugins interact with Totem.  As such, The plugin was enabling, but was not activating the code.  I was able to get the Plugin to launch and 'activate' with the following code under the AirPlayPlugin Class:
> class AirPlayPlugin (GObject.Object, Peas.Activatable):
        __gtype_name__ = "AirPlayPlugin"

        object = GObject.property(type = GObject.Object)

        def __init__ (self):
                GObject.Object.__init__ (self)
                #self.totem = None

        #def activate (self, totem_object):
        def do_activate (self):
               # self.service = AirPlayTotemPlayer(totem=totem_object,name="Totem on %s" % (platform.node()))
                self.service = AirPlayTotemPlayer(totem=self.totem,name="Totem on %s" % (platform.node()))

        #def deactivate (self, totem_object):
        def do_deactivate (self):
                self.service.__del__()



The commented out sections of def activate and def deactivate were the old version.  Adding do_ in front of them made it run.  I had to also remove totem_object to make it work.

If you launch Totem through the command line with totem --debug, you will see AirPlayService now running.  It also shows up in the phone interface as "Totem on %s" but will not actually play video yet.  I think I am going to try to track down what else changed in Totem.

EDIT: I also changed this line in ZeroConfService.py:


                g.AddService(avahi.IF_UNSPEC, avahi.PROTO_UNSPEC,dbus.UInt32(0), self.name, self.stype, self.domain, self.host, dbus.UInt16(self.port), self.text)

Dunno if it did anything though.

---

### Post by rogerrabbitpro on 2011-12-12
Hello everybody.
Facing the same problem.
mine wasn't able to access self.totem in do_activate : ended up adding "self.totem = None" in __init__ and "self.totem = self.object"  in do_activate :


[PHP]        def __init__ (self):
                GObject.Object.__init__ (self)
                self.totem = None

        def do_activate (self):
                self.totem = self.object
                self.service = AirPlayTotemPlayer(totem=self.totem,name="Totem on %s" % (platform.node()))[/PHP]


After that i at least saw a connection attempt (added logging in handle_accept in AirPlayService :

[PHP]      def handle_accept(self):
                print "Accept"
[/PHP]

Still getting errors though :

<type 'exceptions.ValueError'>:dictionary update sequence element #0 has length 1; 2 is required [/usr/lib/python2.7/asyncore.py|read|83

---

### Post by yorba-jim on 2011-12-18
I dug into this this afternoon and got this working.  It's a good news / bad news kind of thing.

First, I've attached a patch that applies to the Totem AirPlay code base as of today.  It uses the code the previous posters supplied (thanks for the boost!) as well as a little extra code to reach the home stretch.  The final problem I ran into was that the URI parsing code wasn't robust enough.

A Big Note: the AirPlay Totem plugin does NOT provide AirTunes support.  It only works as a video player.  AirTunes support would be a lot more work.

What this plugin does is accept a URL (i.e. a YouTube URL) from your iOS device and tell Totem to start playing it.  Yes folks -- it essentially makes your iPhone a Totem remote control.  It does NOT stream video or audio from the iOS device (or iTunes on the desktop) to your computer.  So, be aware of this.

This is a bummer because I was hoping that's exactly what this plugin would do.  No dice.

For those having trouble getting the plugin work at all, make sure you do the following:

* You may need to punch a hole in your firewall.  The plugin is hard-coded to use port 22555.  If all else fails, disable your firewall until you get it working, then re-enable and configure.  Don't ask me how to do this; Google is your friend.

* Also be sure that the Avahi daemon is running.  You can do this from the console:

$ sudo /etc/init.d/avahi-daemon start

(I'm running Fedora on this machine, so it might be different on Ubuntu.)

Finally, pull the code from the original git repo:

$ git clone [http://git.sukimashita.com/totem-plugin-airplay.git](http://git.sukimashita.com/totem-plugin-airplay.git)

and apply the supplied patch:

$ cd totem-plugin-airplay
$ git apply 0001-Updates-to-GNOME-3-libpeas-and-fixes-some-bugs-in-UR.patch

I probably won't support this patch after this, as I'm looking for an audio player and not a video player.  But I wanted to put this out there for those who are looking for one.

---

### Post by TheMunch8 on 2011-12-18
> **yorba-jim said:**
>  Big Note: the AirPlay Totem plugin does NOT provide AirTunes support.  It only works as a video player.  AirTunes support would be a lot more work.

What this plugin does is accept a URL (i.e. a YouTube URL) from your iOS device and tell Totem to start playing it.  Yes folks -- it essentially makes your iPhone a Totem remote control.  It does NOT stream video or audio from the iOS device (or iTunes on the desktop) to your computer.  So, be aware of this

did the original plugin stream from an iOS Device?

---

### Post by guissepi on 2013-03-16
I tried applying the patch but when I try to activate the plugin this is what I get on debug mode :

> jdmg@jdmg:~$ totem --debug

(totem:11494): GLib-WARNING **: /build/buildd/glib2.0-2.34.0/./glib/giounix.c:412Error while getting flags for FD: Descriptor de archivo erróneo (9)

/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
Traceback (most recent call last):
  File "/usr/lib/totem/plugins/airplay/airplay.py", line 30, in <module>
    from AirPlayService import AirPlayService
  File "/usr/lib/totem/plugins/airplay/AirPlayService.py", line 31, in <module>
    from ZeroconfService import ZeroconfService
  File "/usr/lib/totem/plugins/airplay/ZeroconfService.py", line 23, in <module>
    import avahi
ImportError: No module named avahi

(totem:11494): libpeas-WARNING **: Error loading plugin 'airplay'



has anyone managed to get the plugin working on ubuntu 12.10??
Thanks in advance!:p

---

### Post by wildmanne39 on 2013-03-17
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

