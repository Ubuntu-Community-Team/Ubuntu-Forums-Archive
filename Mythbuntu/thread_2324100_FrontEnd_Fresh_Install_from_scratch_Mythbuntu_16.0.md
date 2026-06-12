---
title: "FrontEnd Fresh Install from scratch Mythbuntu 16.04 LTS - Doesn't Work"
date: 2016-05-10
forum: Mythbuntu
---

### Post by griggs2 on 2016-05-10
Let's take a different tack. Mythtv-setup still not working on separate BackEnd - but all else seems to be working... We'll circle back to that.

I decided to wipe the FrontEnd and start from scratch (i was experiencing other system problems with getting Bluetooth to function).

Fresh install using Mythbuntu 16.04 LTS. Running only as FrontEnd.

See simple/short [mythfrontend.log here.]("http://pastebin.com/SFMmPkeF") (just after install)

Full [PasteBin Log Export from MCC here.]("http://pastebin.com/BuJpLfLt")

** Noted issues:**
1 - FrontEnd crashes and restarts after selecting Country and Language and clicking Save (Error 103 display on screen). Cancel also fails to exit.
2 - Mythbuntu Control Centre errors when opening ("Exception in applyStateToGUI of plugin Plugins. Disabling Plugin.")
3 - Mythbuntu Control Centre, unable to uncheck installed Plugins (MythGallery, MythMusic)

Looks to me like this is a build issue or something greater since this was right after rebooting from installing from scratch on a wiped disk.

Any help would be much appreciated.

Thanks much..

---

### Post by gottabefoss on 2016-05-11
> **griggs2 said:**
> 
** Noted issues:**
1 - FrontEnd crashes and restarts after selecting Country and Language and clicking Save (Error 103 display on screen). Cancel also fails to exit.


This may very well be a build issue, as this is a symptom of /etc/mythtv/config.xml having a different password than ~/.mythtv/config.xml

Just cp /etc/mythtv/config.xml ~/.mythtv/config.xml and that (fingers crossed) should fix it.

---

### Post by blm-ubunet on 2016-05-11
Your FE log shows that the PC is setup as 127.0.0.1 localhost ... (isolated combined BE-FE).

The /home/mythtvfe-lr/.mythtvconfig.xml is being used.
There is no usable IP address for the mysql server PC (just 127.0.0.1).

I would use synaptic package manager to install myth-plugins packages & manually edit config.xml file so it contains the right mysql server IP (your mysql server is 10.0.0.70, there is only 1 per mythtv system).

Did you try running mythtv-setup -v upnp,http --loglevel=debug ?

---

### Post by griggs2 on 2016-05-11
gottabefoss -

unfortunately they match... so that's not it.

Do the devs/maintainers for Mythbuntu pay attention to this forum?

---

### Post by griggs2 on 2016-05-11
> [COLOR=#000000]Your FE log shows that the PC is setup as 127.0.0.1 localhost ... (isolated combined BE-FE).[/COLOR]

[COLOR=#000000]The /home/mythtvfe-lr/.mythtvconfig.xml is being used.[/COLOR]
[COLOR=#000000]There is no usable IP address for the mysql server PC (just 127.0.0.1).[/COLOR]

[COLOR=#000000]I would use synaptic package manager to install myth-plugins packages & manually edit config.xml file so it contains the right mysql server IP (your mysql server is 10.0.0.70, there is only 1 per mythtv system).[/COLOR]

[COLOR=#000000]Did you try running mythtv-setup -v upnp,http --loglevel=debug ?[/COLOR]

yes. and mythtv-setup *will not run *on the backend. It crashes with no logging. Previously I was getting no db errors as described in my other thread. As others are describing the same issue -The upgrade to 0.28 borked something. I will try running cmd again on BE and report back in the other thread.

Just curious - are you thinking that whatever the something that is messed up on the BE is why the FE isn't starting properly?

---

### Post by tgm4883 on 2016-05-11
> **griggs2 said:**
> yes. and mythtv-setup *will not run *on the backend. It crashes with no logging. Previously I was getting no db errors as described in my other thread. As others are describing the same issue -The upgrade to 0.28 borked something. I will try running cmd again on BE and report back in the other thread.

Just curious - are you thinking that whatever the something that is messed up on the BE is why the FE isn't starting properly?

Can you paste your ~/.mythtv/config.xml file here.

---

### Post by griggs2 on 2016-05-11
> Can you paste your ~/.mythtv/config.xml file here.

_**FrontEnd:**_
```
<Configuration>
  <Database>
    <PingHost>1</PingHost>
    <Host>localhost</Host>
    <UserName>mythtv</UserName>
    <Password>Q8X5bnFs</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>
```

---

### Post by blm-ubunet on 2016-05-13
A FE using that config.xml can **only work** if the mysql server is also running on the same computer.
I'm fairly sure your mysql server is **not **running on this FE computer..

Change localhost to 10.0.0.70 & then the FE will able to find mythtv's dB server.

Can you also post the config.xml from the BE computer: path /home/mythtv/.mythtv/config.xml ?

---

### Post by griggs2 on 2016-05-13
blm-ubunet, et al

We finally have success with the FrontEnd!

After fixing the config.xml file per blm-ubunet - I started making progress with the other issues on the FrontEnd. 

I had to struggle thru remembering all the steps for getting the video and audio to work, but eventually hit on the winning combinations.

So where did I go wrong?

 First off I was under the impression (and this may have been in an older version, or I was just mis-remembering) that either the Front-End would find the BackEnd by UPnP or that I would get the set-up screen and key in the pertinent DB connection information after selecting Language and Country. I don't  remember (heck it was three years ago when I first got the system working!), whichever, the FrontEnd is working now.

Note that the MCC (Mythbuntu Control Centre) is still a mess and throws up errors and doesn't fully work, but at this point, I've worked thru that - I'll hope an eventual update resolves MCC's operability.

Thanks much to every who pitched in on this... (now back the BackEnd issues (in my other thread))...

./g2

---

