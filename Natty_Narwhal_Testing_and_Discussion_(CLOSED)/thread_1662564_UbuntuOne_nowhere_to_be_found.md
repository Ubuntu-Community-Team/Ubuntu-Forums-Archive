---
title: "UbuntuOne nowhere to be found"
date: 2011-01-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tokyobadger on 2011-01-08
Just installed a new instance of 11.04_amd64-alpha1 in VirtualBox4.0 with Guest Additions on Intel Mac (x86_64 environment) OSX 10.6.6. Updated and am at 2.6.37-12-generic. 3D acceleration working, mostly fine (Skype install fails, but that's for another thread; same gwibber issue with /usr/lib/python2.7/dist-packages/webkit/_init_.pyc, fixed) but UbuntuOne is nowhere.

4 days ago I was working with the same install but on 2 real boxes (also amd64) but I guess at 2.6.37-10-generic (no way to check as those boxes are on the other side of the planet) and UbuntuOne was fine.

Is it 
a) just me?
b) VBox install specific?
c) something others have run into?

Had a look at launchpad but couldn't see anything similar. So I ran the following:
```
badger@badger-VirtualBox:~$ u1sdtool --status
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE

```and presto up pops the UbuntuOne configuration dialogue. Now I have a UbuntuOne folder in ~/ and an icon in the Unity launcher.

So yes it can be fixed, but would be nice for others (maybe?) not to have to rummage around in the CLI to make it work.

Before I post a bug in launchpad, anyone care to confirm 
a) the same in a real install
b) the same in a VBox machine

Thanks

**edit** well a few views a not a lot of input ... so I rebooted the VM; the U1 folder is still there but I have nothing in Control-Centre, nothing in the me-menu indicator. I looked in Synaptic and checked a few U1-related boxes to install. Nothing changed on restart. Except that when I opened a term and tabbed (for completion on the entry ubuntuone) I now got ubuntuone-control-panel-gtk, admittedly one of the packages I marked for installation. When you run that you get an under-construction control-panel that looks like it's going to be nice; running the earlier command (shown in code block above) I get:
```
badger@badger-VirtualBox:-$ u1sdtool --status
State: QUEUE_MANAGER
       connection: With User With Network
       description: procession queues
       is_connected: True
       is_error: False
       is_online: True
       queues: IDLE

```
So I guess the latest updates have put UbuntuOne-related libs into the mixer and we'll just have to wait?

---

### Post by ronacc on 2011-01-10
I don't think ubuntuone knows a network connection if its bitten by one (see SS) I am on maverick for this one and most assuredly have a working connection or else I posted this by osmosis . also this is an install not VB .

---

### Post by tokyobadger on 2011-01-11
@ronacc: thanks for the feedback and the screenshot. On my 10.10_amd64 install (not VBox) and 11.04_amd64-alpha1 install (also not VBox) on a machine on the other side of the planet, UbuntuOne was working fine. This VBox 11.04 install and the 'real' VBox install were done within 72 hours of each other so that led me to consider differing factors such as VBox.

However as you'll note, my problem differs from yours in that the U1 service is fine, I just seem to be missing some pieces like the icon and the launcher.

Let's see what February brings us. UbuntuOne is not a cornerstone of my online life as of today so I'll survive. However, reading through bug reports on launchpad, particularly those where users have paid for extended space or have purchased music through the U1 music store, you'd have to say they will have to get this fixed ASAP or Canonical's cloud initiative will be dead in the water.

**edit:** I now have the Ubuntu One icon in the app folder. Clicking it brings up the ubuntuone-control-panel-gtk that I mentioned above. Under the services tab, which was blank before, I get a message saying I need to install desktopcouch-ubuntuone with a click to install button. Clicking the button results in a failed to install message. By apt at CLI I get unable to locate package and it's not in synaptic either. Looks like my previous conclusion was correct - we'll just have to wait.

---

### Post by Borgoz on 2011-01-11
New interface

[http://www.youtube.com/watch?v=bewWYaXQsuQ](http://www.youtube.com/watch?v=bewWYaXQsuQ)

---

### Post by Framli on 2011-01-11
Launchpad project for this new interface

[https://launchpad.net/ubuntuone-control-panel](https://launchpad.net/ubuntuone-control-panel)

---

### Post by ratcheer on 2011-01-11
How does one start this new interface? I cannot find it in any of the menus.

Tim

---

### Post by mc4man on 2011-01-11
if you actually have installed then - 

/usr/share/applications > Ubuntu One
or in terminal
ubuntuone-control-panel-gtk
or look in System > Preferences

---

### Post by ratcheer on 2011-01-11
Thank you, mc4man. It was not installed on my system. No wonder I couldn't find it!

Tim

---

### Post by mc4man on 2011-01-11
Went ahead and hooked it up to existing ubuntu one account from maverick and it works, for the moment, surprisingly well.

---

