---
title: "Problem with banshee and DBus"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by palimmo on 2007-06-05
May you help me?

[I]:~$ sudo banshee
Password:
Warning: [05/06/2007 20.30.45] (DBus is not available) - Your environment is not properly set up to use DBus. Please fix your environment or run Banshee through dbus-launch. Failure to do so may cause problems at a later time in Banshee during this instance.

Unable to open the session message bus.
System.Exception: Unable to open the session message bus. ---> Mono.Unix.UnixIOException: Pipe interrotta [EPIPE].
  at Mono.Unix.UnixMarshal.ThrowExceptionForLastError () [0x00000]
  at Mono.Unix.UnixStream.Write (System.Byte[] buffer, Int32 offset, Int32 count) [0x00000]
  at NDesk.DBus.Connection.WriteMessage (NDesk.DBus.Message msg) [0x00000]
  at NDesk.DBus.Connection.Send (NDesk.DBus.Message msg) [0x00000]
  at NDesk.DBus.Connection.SendWithReply (NDesk.DBus.Message msg) [0x00000]
  at NDesk.DBus.Connection.SendWithReplyAndBlock (NDesk.DBus.Message msg) [0x00000]
  at NDesk.DBus.BusObject.Invoke (System.Reflection.MethodBase methodBase, System.String methodName, System.Object[] inArgs, System.Object[]& outArgs, System.Object& retVal, System.Exception& exception) [0x00000]
  at NDesk.DBus.DProxy.Invoke (IMessage message) [0x00000]
  at System.Runtime.Remoting.Proxies.RealProxy.PrivateInvoke (System.Runtime.Remoting.Proxies.RealProxy rp, IMessage msg, System.Exception& exc, System.Object[]& out_args) [0x00000] --- End of inner exception stack trace ---

  at NDesk.DBus.Bus.get_Session () [0x00000]
  at Banshee.Base.DBusPlayer.FindInstance () [0x00000]
  at Banshee.BansheeEntry.DetectInstanceAndDbus () [0x00000]
Warning: [05/06/2007 20.30.46] (Could not connect to D-Bus) - D-Bus support will be disabled for this instance: Unable to open the session message bus.[/I]

---

### Post by palimmo on 2007-06-06
:(

---

### Post by tgalati4 on 2007-06-06
Why are you running Banshee with sudo?  You should be able to run it as a normal user.

It looks like  your Banshee install is borked.  Was it ever working properly?  Try reinstalling in Synaptic.  What version of Ubuntu are you using?

---

### Post by palimmo on 2007-06-06
I've tried it as a normal user, too. But nothing.
I've tried to reinstall it, but nothing.
I've ubuntu 7.04.

Help please!:(

---

### Post by palimmo on 2007-06-06
help please!

---

### Post by palimmo on 2007-06-06
I've tried to reinstall dbus from synaptic.... but then nothing is changed
:cry:

---

### Post by palimmo on 2007-06-07
if it is useful:
[I]
:~$ ls /etc/rc2.d
README                       S19hplip          S89atd
S05vbesave                   S20apmd           S89cron
S10acpid                     S20apport         S90binfmt-support
S10powernowd.early           S20hotkey-setup   S98usplash
S10sysklogd                  S20makedev        S99acpi-support
S10xserver-xorg-input-wacom  S20nvidia-kernel  S99rc.local
S11klogd                     S20powernowd      S99rmnologin
S12dbus                      S20rsync          S99stop-readahead
S13gdm                       S25bluetooth
S19cupsys                    S89anacron
[/I]
and also:

[I]:~$ sudo /etc/init.d/dbus restar
Usage: /etc/init.d/dbus {start|stop|reload|restart|force-reload}[/I]

---

### Post by akwatve on 2008-01-11
I do get the similar dbus error. But banshee plays my media files....
I am using kubuntu gutsy.


Here is the complete output. Hope the wiser folks can understand whats happening here...


Warning: [1/11/2008 3:01:01 PM] (DBus is not available) - Your environment is not properly set up to use DBus. Please fix your environment or run Banshee through dbus-launch. Failure to do so may cause problems at a later time in Banshee during this instance.

Unable to open the session message bus.
System.Exception: Unable to open the session message bus. ---> System.ArgumentNullException: Argument cannot be null.
Parameter name: address
  at NDesk.DBus.Bus.Open (System.String address) [0x00000]
  at NDesk.DBus.Bus.get_Session () [0x00000] --- End of inner exception stack trace ---

  at NDesk.DBus.Bus.get_Session () [0x00000]
  at Banshee.Base.DBusPlayer.FindInstance () [0x00000]
  at Banshee.BansheeEntry.DetectInstanceAndDbus () [0x00000]
Warning: [1/11/2008 3:01:02 PM] (Could not connect to D-Bus) - D-Bus support will be disabled for this instance: Unable to open the session message bus.
Debug: [1/11/2008 3:01:02 PM] (Loading audio profiles) - /usr/share/banshee/audio-profiles
Debug: [1/11/2008 3:01:03 PM] (Default player engine) - GStreamer 0.10
Debug: [1/11/2008 3:01:03 PM] (Audio CD Core Initialized) -
Warning: [1/11/2008 3:01:03 PM] (Power Management Call Failed) - Cannot find GNOME Power Manager: Unable to open the session message bus.
Setting IO Backend to Banshee.IO.Unix.IOConfig (unix)

---

### Post by akwatve on 2008-01-11
One more quick comment.... I run banshee as a normal user , not as sudo

---

### Post by BenHines on 2008-02-03
Has anyone ever figured this one out?  I prefer Banshee, but am having the same DBus problem when I run under Kubuntu.

---

### Post by tgalati4 on 2008-02-03
I do get the same error when I run banshee through a remote terminal.  Normally I do this to activate music shares on that machine.  A workaround for me is:

>dbus-launch banshee --debug

Perhaps your installation is broken or you are logging into a remote machine even though you are on the same physical machine.

---

### Post by akwatve on 2008-02-03
well............ i never used banshee using remote terminal but still I used to get the error. I think when something breaks, adept shows it. But in this case, it did not show any error suggesting a broken package. 
BTW Amarok is pretty cool .... In fact I like to more than banshee. may be ppl who are having trouble with banshee should give a try to amarok

---

### Post by cybersmoker on 2008-07-04
Me TOO! The user interface is alittle more than I am used to but alot of great features. Thanks for the tip.:guitar:

---

