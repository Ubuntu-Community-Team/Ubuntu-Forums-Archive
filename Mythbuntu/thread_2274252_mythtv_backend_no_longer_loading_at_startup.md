---
title: "mythtv backend no longer loading at startup"
date: 2015-04-19
forum: Mythbuntu
---

### Post by sylvester3 on 2015-04-19
Hope some on here can help with this.

I've spent the last few months setting up mythbuntu to work just the way I wanted:

-setup rtc wakeup to turn PC on for recordings
-setup mythwelcome to start the frontend when no recordings are scheduled
-shutdown when recording is complete and frontend is not running
-configure lirc to close frontend when user presses power button on remote control

I was happy using this setup for a few weeks, with one exception - often a prompt would come up asking for root password for the wifi connection. I think trying to fix this has somehow broken something.

I've read about networking issues in forums and I can't remember exactly how I did it, but it was something to do with removing the password for the default keyring.

I think that worked for a while, although if my memory is correct I think I remember at times the machine did not shut down after a recording. I shut down and removed the power cable while I went away on holidays.

Since I returned from holidays I've seen a new prompt for password come up - this time it was to do with "[COLOR=#3A453B][FONT=Lucida Grande]org.freedesktop.NetworkManager.policy[/FONT][/COLOR]". I googled and followed the advice at [http://community.linuxmint.com/tutorial/view/1035](http://community.linuxmint.com/tutorial/view/1035) and edited [COLOR=#3A453B][FONT=Lucida Grande]/usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy[/FONT][/COLOR] (changed [COLOR=#3A453B][FONT=Lucida Grande]<allow_active>auth_admin_keep</allow_active>[/FONT][/COLOR] to [COLOR=#3A453B][FONT=Lucida Grande]<allow_active>yes</allow_active>[/FONT][/COLOR]).

Now I'm no longer prompted for passwords but the mythtv backend never starts. I'm pretty sure that messing around with Network settings is the cause as I haven't made any other changes.

If I run "sudo service mythtv-backend start" at the command line manually, then everything works as expected.

How can I troubleshoot this? /var/log/mythtv/mythtvbackend.log reveals nothing and I've tried adding echo statements to the startup script as mentioned at [http://lists.mythtv.org/pipermail/mythtv-users/2014-February/360338.html](http://lists.mythtv.org/pipermail/mythtv-users/2014-February/360338.html) but I must have stuffed it up as this caused errors.

Also does anyone know of any good guide to configuring the networking? I've haven't been able to find anything specific to my needs.

Thanks, if you've read this far :)

---

### Post by sylvester3 on 2015-04-19
I *think* the issue is resolved. Myth backend was not starting as the Network was not available at boot.

I noticed there is an option under Users and groups -> Advanced -> User Privileges called "Connect to wireless and ethernet networks".

This option was unchecked. I enabled it, then removed and reconfigured the wifi connection.

Now I have Network (no password prompts at all) and MythTV works as before.

Still couldn't get the startup script to write to a log file, no matter what I tried.

Hopefully all is well and won't have such big problems in the future.

---

