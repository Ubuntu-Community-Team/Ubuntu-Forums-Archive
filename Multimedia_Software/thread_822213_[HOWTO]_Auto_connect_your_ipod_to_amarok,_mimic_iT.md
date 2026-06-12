---
title: "[HOWTO] Auto connect your ipod to amarok, mimic iTunes functionality"
date: 2008-06-08
forum: Multimedia Software
---

### Post by richter on 2008-06-08
My Amarok doesn't automatically pick up my ipod classic (6G) has been connected. Perhaps this is by design or a flaw in my install. Here's how I changed that behavior. 

1. Add Amarok as available music player.
```
gksudo gedit /usr/share/applications/kde/amarok.desktop
```

Add this to the end of MimeType at the bottom of the file ```
x-content/audio-player;
```
This has been filed as bug [#208197]("https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/208197"). Step might not be necessary in the future.

2. Change ```
Exec=amarok %U
``` to ```
Exec=/usr/local/bin/amarok.pl
``` Save and exit.

3. Create amarok.pl ```
gksudo gedit /usr/local/bin/amarok.pl
```Paste the following:```
#!/usr/bin/perl
$running=`/bin/ps aux | grep amarok | grep -v grep | grep -v amarok.pl | wc -l`;
chomp $running;
if ( $running > 0 ) {
        `dcop amarok mediabrowser deviceConnect`;
} else {
        `amarok`;
};


```Save and exit.

4. ```
sudo chmod a+x /usr/local/bin/amarok.pl
```

5. Log out and back in, this is to reset nautilus. Launch nautilus and go to Edit->Preferences->Media->Music Player. You should now have an option for amarok. Select that and click Close.

You should now be able to connect your ipod and it will launch amarok and connect. If amarok is already running, it will initiate a connection to the ipod. Please feel free to clean up that perl script and post to the thread. Thanks.

---

### Post by lottes70 on 2008-12-28
It did not work for me. I'm running 8.04 hardy heron.

Everything seemed to 'work' as I put it in, but when I logged out and back in, then went to Edit->Preferences->Media->Music Player Amarok was not among the choices, only Rhythmbox.

When I plug the nano in, the application Music Player opens (paused).

---

