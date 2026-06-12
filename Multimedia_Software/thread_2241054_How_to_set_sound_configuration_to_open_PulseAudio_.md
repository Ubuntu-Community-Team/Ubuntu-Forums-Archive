---
title: "How to set sound configuration to open PulseAudio Volume Control"
date: 2014-08-23
forum: Multimedia Software
---

### Post by thiago-canaes on 2014-08-23
Greetings!

I wanted to be able to set each app to a specific oudio output. 
On Xubuntu, I could do that with the normal sound configuration, but, on Ubuntu, I had to install PAVUCONTROL.

Now, Id like to know how to make the PAVUCONTROL the default sound configuration tool.
Is is possible? To set the audio indicator on the top right to open the PAVUCONTROL?

Im using Ubuntu 14.04.

Tnks in advance.
TC.

---

### Post by mc4man on 2014-08-23
If you are referring to setting the sound indicator to open pavucontrol  - 
it has to be done in the source, very simple change.

I've been using that for some time,  14.04 packages are in my personal ppa but I don't particularly recommend anyone using.  So placed in a standalone ppa, 

[https://launchpad.net/~mc3man/+archive/ubuntu/sound1](https://launchpad.net/~mc3man/+archive/ubuntu/sound1)

---

### Post by thiago-canaes on 2014-08-23
COOL! 
Do i need to unninstall anything before installing your indicator, or it will replace the current one ?

EDIT ->
Ubuntu Software Center displayed as an update. It replaced the old one.
Tnks a lot!

---

### Post by mc4man on 2014-08-23
> **thiago-canaes said:**
> COOL! 
Do i need to unninstall anything before installing your indicator, or it will replace the current one ?

No, it will install it as an upgrade to current one.

---

### Post by mc4man on 2014-08-23
na

---

### Post by goundoulf on 2014-08-30
> **mc4man said:**
> I've been using that for some time,  14.04 packages are in my personal ppa but I don't particularly recommend anyone using.  So placed in a standalone ppa, 

[https://launchpad.net/~mc3man/+archive/ubuntu/sound1](https://launchpad.net/~mc3man/+archive/ubuntu/sound1)

Why don't you recommend it?

I've installed your package, but I see no difference, what change did you make in the source ? Thanks a lot.

---

### Post by mc4man on 2014-08-30
> **goundoulf said:**
> Why don't you recommend it?

I've installed your package, but I see no difference, what change did you make in the source ? Thanks a lot.
I was referring [to here]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-prop") as most of the changes are quite specific to me. (and the indicator-sound package has been removed anyway

As far as the indicator-sound package in the sound1 ppa these are the changes. If you upgraded to that package & log out/in or restart you'll get pavucontrol from the sound indicator instead of ubuntu's sound panel

```
diff -u indicator-sound-12.10.2+14.04.20140401/debian/control indicator-sound-12.10.2+14.04.20140401/debian/control
--- indicator-sound-12.10.2+14.04.20140401/debian/control
+++ indicator-sound-12.10.2+14.04.20140401/debian/control
@@ -24,7 +24,7 @@
                libgee-dev,
                libxml2-dev,
                python3-dbusmock,
-Standards-Version: 3.9.4
+Standards-Version: 3.9.5
 Homepage: https://launchpad.net/indicator-sound
 # If you aren't a member of ~indicator-applet-developers but need to upload
 # packaging changes, just go ahead.  ~indicator-applet-developers will notice
@@ -37,8 +37,9 @@
 Depends: ${shlibs:Depends},
          ${misc:Depends},
          pulseaudio,
+         pavucontrol,
          gsettings-ubuntu-schemas (>= 0.0.1+14.04.20140224),
-Recommends: unity-control-center | gnome-control-center | ubuntu-system-settings | pavucontrol,
+Recommends: unity-control-center | gnome-control-center | ubuntu-system-settings,
             accountsservice,
 Suggests: unity-greeter-session-broadcast,
 Description: System sound indicator.
only in patch2:
unchanged:
--- indicator-sound-12.10.2+14.04.20140401.orig/src/service.vala
+++ indicator-sound-12.10.2+14.04.20140401/src/service.vala
@@ -206,7 +206,7 @@
 	void activate_desktop_settings (SimpleAction action, Variant? param) {
 		var env = Environment.get_variable ("DESKTOP_SESSION");
 		string cmd;
-		if (env == "xubuntu" || env == "ubuntustudio")
+		if (env == "ubuntu" || env == "ubuntustudio" || env == "xubuntu")
 			cmd = "pavucontrol";
 		else
 		{

```

---

### Post by goundoulf on 2014-08-31
Thanks for your quick answer. I am running Xubuntu, that's why I didn't see any changes :)

---

