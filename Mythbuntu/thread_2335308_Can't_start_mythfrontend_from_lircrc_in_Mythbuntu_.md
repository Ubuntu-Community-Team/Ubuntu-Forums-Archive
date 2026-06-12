---
title: "Can't start mythfrontend from lircrc in Mythbuntu 16.04"
date: 2016-08-27
forum: Mythbuntu
---

### Post by jzig on 2016-08-27
I have a script that will start mythfrontend when run from the command line, but when that script is called from within lircrc via "irexec", both "top" and "ps aux" show that it's running, but the display never changes to mythtv, it just keeps showing me the desktop.

I have reduced the script to a one liner for debugging purposes:
```
#xorgDFP.sh
sudo -u ziggy /usr/bin/mythfrontend --service
```
This is the call from lircrc"
```
begin
    prog = irexec
    button = s6
    # script to change brightness
    config = /home/mythtv/zig/xorgDFP.sh  
end
```
I  also tried to start mythfrontend directly from lircrc with:
```
begin
    prog = irexec
    button = s1
    # script to change brightness
    config = su ziggy -c 'mythfrontend --service &'
end
```this produces the same result.  Top shows it's running, but mythtv is not displayed on the screen.

As a side note, the mythbuntu control center produces a pre-canned lircrc that has a "restart mythfrontend" button defined as:
```
begin
    prog = irexec
    button = s8
    config = (kill $(pgrep mythfrontend) || true) && mythfrontend --service &
end
```It doesn't work either.  It does stop the running frontend but it doesn't restart it at all, it doesn't show up as running in top either.

How can I start (or restart) mythfrontend with a remote button press in Mythbuntu 16.04?
Thanks.

---

### Post by nexzzt on 2016-08-29
Hello,

Try this in your script:

```
DISPLAY=:0 mythfrontend --service &
```

I had the same issue and found you have to specify the display when executing commands that run in the GUI via LIRC.

EDIT: This also assumes you want mythfrontend to be launched in DISPLAY 0 (which I believe is the norm). Your set up maybe different

Cheers
Ben

---

### Post by jzig on 2016-08-29
Thanks, Ben!  You have no idea how many things I've tried to get this working.  It didn't work straight away, but did work after switching users.  This is the new script that works for me when called from lircrc:
```
su ziggy -c 'DISPLAY=:0 mythfrontend --service &'
```

---

### Post by nexzzt on 2016-08-29
Sorry, I should have tailored the command suit to your set up. Anyway you got there in the end, good stuff!

Cheers
Ben

---

