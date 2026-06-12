---
title: "Delay myth FE until wifi connected"
date: 2009-12-13
forum: Mythbuntu
---

### Post by tonycollinet on 2009-12-13
Hi

Just set up a front end, with wifi connection to backend. Problem is the myht FE starts before the wifi is established, and complains that the b/e cannot be found.

Is there a way of delaying the fe startup until wifi is set up.

Thanks.

---

### Post by gslug79 on 2009-12-13
If you have the standard Mythbuntu install - i.e. an Xfce desktop, Mythfrontend is started by the following file: /home/username/.config/autostart/mythtv.desktop. The contents of this file will be:

```
[Desktop Entry]
Name=MythTV Frontend
Comment=A frontend for all content on a mythtv-backend
GenericName=MythTV Viewer
Exec=mythfrontend --service
Type=Application
Encoding=UTF-8
Icon=/usr/share/mythtv/themes/MythCenter-wide/ui/mythtv_logo.png
Categories=GNOME;Application;AudioVideo;Audio;Video
X-AppInstall-Package=mythtv

```

To add a delay, you can create a script called for example mythdelay.sh, containing the following:

```
#!/bin/sh
sleep 15
/usr/bin/mythfrontend
```

Where the number after sleep is the number of seconds to wait before starting the frontend. You may need to change this to suit your system.

Save this script wherever you like and make it executable with chmod a+x mythdelay.sh. I put mine in /usr/bin

Finally change /home/username/.config/autostart/mythtv.desktop so that instead of starting the frontend directly, it runs the new script:

```
[Desktop Entry]
Name=MythTV Frontend
Comment=A frontend for all content on a mythtv-backend
GenericName=MythTV Viewer
Exec=/usr/bin/mythdelay.sh **(or alternative path to mythdelay.sh)**
Type=Application
Encoding=UTF-8
Icon=/usr/share/mythtv/themes/MythCenter-wide/ui/mythtv_logo.png
Categories=GNOME;Application;AudioVideo;Audio;Video
X-AppInstall-Package=mythtv

```

Hope this helps

---

### Post by tonycollinet on 2009-12-13
Brilliant - thanks, I'll give it a go.


Edit: - excellent - now works, thanks.

---

### Post by one30nav on 2012-08-19
Thanks for sharing this.

In the example above, in the mythdelay.sh bash script, you should include "--service." Otherwise, you won't receive any mythfrontend.log entries.

So, use:

```
#!/bin/sh
sleep 15
/usr/bin/mythfrontend --service
```

Cheers, Al

---

### Post by overdrank on 2012-08-19
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

