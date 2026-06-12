---
title: "Mythbuntu &quot;official&quot; way to restart frontend from remote"
date: 2011-06-17
forum: Mythbuntu
---

### Post by brenthaag on 2011-06-17
I have searched multiple sites, including this one, to find the command that is supposed to be in one of the LIRC files. In Mythbuntu Control Center, the option to add the frontend restart button mapping doesn't work on 11.04.

So, what I was wondering is: what is the official script that this would run? I can put that in my lirc configuration file, but want to know. Otherwise, I will just make up my own.

Thanks.

---

### Post by ian dobson on 2011-06-20
Hi,

I don't think there's an office script for this. You can do it what ever way you like.

For me I just patched mythfrontend (the script that starts mythfrontend.real) so that it just loops and starts the frontend again. Note this solution could get overwritten when updates are installed.

Regards
Ian Dobson

---

### Post by dibuntux on 2011-06-20
I believe is more than a year that they introduced automatic frontend restart. I'm running 0.24 on 10.04 AMD64 with latest PPA: when (rarely) the frontend crash, I'm back in Xfce desktop and a message in the notification bar says "the frontend has crashed unexpectedly and is been restarted". And I've done nothing to implement this.

---

### Post by ian dobson on 2011-06-20
> **dibuntux said:**
> I believe is more than a year that they introduced automatic frontend restart. I'm running 0.24 on 10.04 AMD64 with latest PPA: when (rarely) the frontend crash, I'm back in Xfce desktop and a message in the notification bar says "the frontend has crashed unexpectedly and is been restarted". And I've done nothing to implement this.

I think what your talking about is apport :- [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

Regards
Ian Dobson

---

### Post by dakota34 on 2011-06-20
automatic restart & the notification popup after a frontend crash is now built into the /usr/share/mythtv/mythfrontend.sh script, around line 80 I think.  You may find this does all you need. Personally I find this interferes with WAF, bcs the problem my family encounters most frequently isn't frontend crashing, it's the frontend freezing. And the mythfrontend.sh auto-restart/notify intereferes with the solution we've always used for freezing, which is a simple power-button-trigerred stop and start of mythfrontend via irexec. So I comment out the auto-restart & notify lines in /usr/share/mythtv/mythfrontend.sh so we can keep using a power-button-triggerred restart accomplished by using the following in ~/.lirc/irexec: 

```
begin
    remote = mceusb
    prog = irexec
    button = Power
    config = killall mythfrontend.real && mythfrontend --service &
    repeat = 0
    delay = 0
end
```

Problem is now, the mythfrontend.sh gets replaced with updates, so i now keep a copy of the commented-out version in the same folder and simply remove and replace mythfrontend.sh with every update. If I were less of a dolt I would be able to automate it. but like everyone, I'm doing what I can. Cheers.

:p

---

### Post by brenthaag on 2011-06-25
> **dakota34 said:**
> automatic restart & the notification popup after a frontend crash is now built into the /usr/share/mythtv/mythfrontend.sh script, around line 80 I think.  You may find this does all you need. Personally I find this interferes with WAF, bcs the problem my family encounters most frequently isn't frontend crashing, it's the frontend freezing. And the mythfrontend.sh auto-restart/notify intereferes with the solution we've always used for freezing, which is a simple power-button-trigerred stop and start of mythfrontend via irexec. So I comment out the auto-restart & notify lines in /usr/share/mythtv/mythfrontend.sh so we can keep using a power-button-triggerred restart accomplished by using the following in ~/.lirc/irexec: 

```
begin
    remote = mceusb
    prog = irexec
    button = Power
    config = killall mythfrontend.real && mythfrontend --service &
    repeat = 0
    delay = 0
end
```

Problem is now, the mythfrontend.sh gets replaced with updates, so i now keep a copy of the commented-out version in the same folder and simply remove and replace mythfrontend.sh with every update. If I were less of a dolt I would be able to automate it. but like everyone, I'm doing what I can. Cheers.

:p

I totally agree with it not "crashing", but freezing.  Now, my problem is that irexec won't run...more troubleshooting to be done.  Also, I think I found the official script MCC should put in:

```

(kill $(pgrep mythfrontend) || true) && mythfrontend --service &

```

---

### Post by mikulator on 2012-01-20
I just want to add that I have implemented the following and it works in mythbuntu 11.10.

Comment out 2 lines in /etc/share/mythtv/mythfrontend.sh they are at the end of the script arround line 80

```

...
          do
#             echo “Restarting mythfrontend.real…” >> “¤{MYTHFELOG}”
#             notify-send -I info ‘Restarting Frontend’ “The front-end crash…
          done
...

```

Then add the following to /home/<user>/.lirc/mythtv

```
begin
    remote = <put in your remotes is>
    prog = irexec
    button = <put in your buttons id>
    config = (kill $(pgrep mythfrontend) || true) && mythfrontend --service &
    repeat = 0
    delay = 0
end
```

Using the above solved a real big (serious WAF damaging) problem I was having with all other methods I tried which involved myth restarting several mythfrontend.real then killing them again and restarting them again in a continuous loop.

---

### Post by kingmoffa on 2012-05-18
Does this work in 12.04?

I'm having trouble with my shell scripts :

killall -9 mythfrontend.real 
killall -9 mythfrontend

Do not seem to work.

---

### Post by Quazza on 2012-06-12
Hi Guys,

I'm having the same trouble and was wondering if anyone has a similar piece of this puzzle for 12.04 as the script for mythfrontend.sh seems to have changed ever so slightly?

Any help would be greatly appreciated

Cheers

Quazza :D

---

### Post by Quazza on 2012-06-12
Hi Again,

I have managed to fix my problem with advice from one of the guys from [www.pcmediacenter.com.au](www.pcmediacenter.com.au) - Thanks rileyp  anyway I did the below and mythfrontend is no longer launching in a loop.

In 

/usr/share/mythtv/mythfrontend.sh

Went to the bottom of the file and commented out this line

# exec /usr/bin/mythfrontend.real --syslog local7 "$@"

and now the mythfrontend loop is gone , only problem is that Mythfrontend won't auto start now but thats alright I am going to have XBMC autostart instead anyway, unless someone knows how to fix that ?

Cheers

Quazza :D

---

### Post by nickrout on 2012-06-12
> **Quazza said:**
> Hi Again,

I have managed to fix my problem with advice from one of the guys from [www.pcmediacenter.com.au](www.pcmediacenter.com.au) - Thanks rileyp  anyway I did the below and mythfrontend is no longer launching in a loop.

In 

/usr/share/mythtv/mythfrontend.sh

Went to the bottom of the file and commented out this line

# exec /usr/bin/mythfrontend.real --syslog local7 "$@"

and now the mythfrontend loop is gone , only problem is that Mythfrontend won't auto start now but thats alright I am going to have XBMC autostart instead anyway, unless someone knows how to fix that ?

Cheers

Quazza :D

If you comment out the line that starts mythfrontend then clearly it won't start.

---

### Post by tgm4883 on 2012-06-12
> **nickrout said:**
> If you comment out the line that starts mythfrontend then clearly it won't start.

+1 to this. It sounds like whoever gave you the advice they did is either super lazy or has no idea what they are doing in bash scripts. A better solution if you wanted to stop the automated restart is to remove the loop. An even better solution is to figure out what return code you don't want it to restart on and add that to the list.

---

### Post by dheianevans on 2012-08-03
Thomas in the Myth list told me to check off "Generate frontend restart mapping" in Mythbuntu Control Centre. A restart later and I could restart/start the frontend by hitting Power then Clear.

---

### Post by paubyuk on 2012-09-08
This is a couple of months old now but I've just come across it and need some help. I am using Ubuntu 10.10.

Basically, what has been suggested simply does not work for me. When I implement it, the button I am using does nothing. Nothing happens.

I have amended the /home/tv/.lirc/mythtv file and added this at the start:

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Record
    config = (kill $(pgrep mythfrontend) || true) && mythfrontend --service &
    repeat = 0
    delay = 0
end

Using the Record button doesn't work. Note:

1. I commented out the OTHER Record button(s) (there were two of them) in this file. It made no difference. The Record button still does nothing.
2. I used the Record button as I KNOW it works (ie. does something). My intention, when I get this working, is to use the Blue teletext button.
3. Using prog = irexec as suggested in this thread does nothing. The other buttons in the file are all prog = mythtv. But I've tried both.
4. I have retarted lirc and the whole system between each change but still the Record button does nothing at all.

In addition the post by mikulator suggests that two lines should be commented out. When I do this mythfrontend no longer starts and give the error about 'unexpected done encountered'. I only commented out the second line and it worked.

---

