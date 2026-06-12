---
title: "nm-applet missing when using NX desktop"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2011-11-08
having set a machine up to be physically inaccessible, then networking is of prime importance.

I have a machine, which I put a clean install of 10.04, Lucid on. And then installed the X2go NX server component.

Connecting in, using the X2Go client, revealed an irritating situation. For some reason, the nm-applet which lives in the top panel was missing.

For anyone who has this problem, IGNORE ANY OTHER ADVICE. It won't work. Here's the scoop.

I managed to get a temporary fix by running :
```
sudo nm-applet --sm-disable

```

in a terminal. Sure enough, the applet would pop up. However, you then discover, that you can't edit any connections. Now I fixed this before, in 9:10 [this]("http://ubuntuforums.org/showthread.php?t=1616355") way. REMEMBER THIS LINK, YOU WILL NEED IT.

However this is not really the best fix.

So, I dug further.

It seems that the presence of the nm-applet is controlled by ConsoleKit, whatever that is. And logging in from the NX protocol manages to not load consolekit into your session. So:

STEP 1: Run ConsoleKit on startup

you need this line in ~/.xinitrc (that's in your home dir)

```
exec ck-launch-session dbus-launch gnome-session
```

I didn't have that file, and needed to create it.

STEP 2:
You need to tell NetworkManager and nm-applet to submit to consolekit

in /etc/dbus-1/system.d/NetworkManager.conf you need to insert the following section. Replace ###### with your username:

```
        <policy user="######">
                <allow own="org.freedesktop.NetworkManager"/>
                <allow own="org.freedesktop.NetworkManagerSystemSettings"/>

                <allow send_destination="org.freedesktop.NetworkManager"/>
                <allow send_destination="org.freedesktop.NetworkManagerSystemSettings"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.PPP"/>
        </policy>
```

a similar edit is needed in /etc/dbus-1/system.d/nm-applet.conf:
```

        <policy user="#####">
                <allow own="org.freedesktop.NetworkManagerUserSettings"/>

                <allow send_destination="org.freedesktop.NetworkManagerUserSettings"
                       send_interface="org.freedesktop.NetworkManagerSettings"/>

                <allow send_destination="org.freedesktop.NetworkManagerUserSettings"
                       send_interface="org.freedesktop.NetworkManagerSettings.Connection"/>

        </policy>
```

STEP 4:

If you have got this far, a logout and log in should demonstrate that the nm-applet is now showing.

Don't get too excited. You can't actually edit connections.

STEP 5:

You now need to add this instance of nm-applet to Polkit. First off, follow the instructions in the thread referred to above. Here's a reminder :[ link]("http://ubuntuforums.org/showthread.php?t=1616355")

then, you need to create a file:

/etc/polkit-1/localauthority/50-local.d/10-org-freedesktop-network-manager-settings.pkla

and add the following, again ###### = your user name:
```

Identity=unix-user:######
Action=org.freedesktop.network-manager-settings.system.modify
ResultAny=yes
ResultInactive=yes
ResultActive=yes
```

logout, login, and you'll find the nm-applet is there *AND* you can edit connections.

This took me 4 hours of experimenting, and googling. Considering my experience of Linux is approaching zero, I feel rightly chuffed with myself. I hope this helps anyone who has had the same frustrations as me.

---

