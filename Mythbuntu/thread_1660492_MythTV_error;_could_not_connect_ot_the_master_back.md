---
title: "MythTV error; could not connect ot the master backend server"
date: 2011-01-05
forum: Mythbuntu
---

### Post by gunsmoke on 2011-01-05
Just installed latest Mythbuntu 10.10. + mythtv 0.24 (thru repository) After I have done the settings in the MythTV Backend setup, I get the following error message:

> Could not connect to the master backend server.Is it running? Is the IP adress set for it in mythtv-setup correct?

The set up is for a single unit BE/FE. IP adress is default 127.0.0.1.


I have installed Mythbuntu with the CD option, and also tried the option with installing mythubuntu ontop of a clean ubuntu 10.10 install, same error.


I have an other setup running ubunut 10.10 +Mythtv 0.23.1 working just fine.


Any sugestion how to resolve this issue?

---

### Post by tgm4883 on 2011-01-05
> **gunsmoke said:**
> Just installed latest Mythbuntu 10.10. + mythtv 0.24 (thru repository) After I have done the settings in the MythTV Backend setup, I get the following error message:



The set up is for a single unit BE/FE. IP adress is default 127.0.0.1.


I have installed Mythbuntu with the CD option, and also tried the option with installing mythubuntu ontop of a clean ubuntu 10.10 install, same error.


I have an other setup running ubunut 10.10 +Mythtv 0.23.1 working just fine.


Any sugestion how to resolve this issue?

Is the backend running?

sudo service mythbackend status  (might be mythtv-backend)

---

### Post by sami8519 on 2011-01-06
This error happens to me every time I start mythbuntu but I press OK button or exit button on the remote control and it just go away.

Edit:Forgot to mention this happened the moment I upgraded to mythbuntu 0.24.

Regards
Sami

---

### Post by ian dobson on 2011-01-06
Hi,

maybe you just need to slowdown the start of the frontend process. Look for the mythfrontend script and just add a sleep x seconds just before it calls mythfrontend.real.

I've seen that my backend takes almost 30 seconds to startup (This is mainly caused by 2 IP tuners that take forever to change channels).

Regards
Ian Dobson

---

### Post by gunsmoke on 2011-01-06
> **tgm4883 said:**
> Is the backend running?

sudo service mythbackend status  (might be mythtv-backend)

Output:
mythbackend: unrecognized service


But using mythtv-backend gives:

@ASUSM3N78:~$ sudo service mythtv-backend status
mythtv-backend start/running, process 15039

---

### Post by gunsmoke on 2011-01-06
> **sami8519 said:**
> This error happens to me every time I start mythbuntu but I press OK button or exit button on the remote control and it just go away.

Edit:Forgot to mention this happened the moment I upgraded to mythbuntu 0.24.

Regards
Sami

On my set up it keeps coming back, and it gives also a warning on the frontend System Status page that says:

> Warning; is mythfilldatabase running?

---

### Post by gunsmoke on 2011-01-06
> **ian dobson said:**
> Hi,

maybe you just need to slowdown the start of the frontend process. Look for the mythfrontend script and just add a sleep x seconds just before it calls mythfrontend.real.

I've seen that my backend takes almost 30 seconds to startup (This is mainly caused by 2 IP tuners that take forever to change channels).

Regards
Ian Dobson

Ian, need some guidlines how to try that. "mythfrontend" is that the name of the script/file? and if so where would it be located?

Bit of a noob afraid..

---

### Post by 4dognight on 2011-01-06
10.10 requires a tuner to be configured, or the backend wont start.

---

### Post by ian dobson on 2011-01-06
> **gunsmoke said:**
> Ian, need some guidlines how to try that. "mythfrontend" is that the name of the script/file? and if so where would it be located?

Bit of a noob afraid..

OK,

So you need to edit the following file:-  /usr/bin/mythfrontend
with your fav. text editor (I use nano from the terminal) and look for the line 

pidof mythfrontend.real 2>&1 >/dev/null && wmctrl -a "MythTV Frontend" 2>/dev/null && exit 0

now add a new line just before the pidof and add the following:
sleep 10

so the start of the file should look like:-

```
#!/bin/sh
# Mario Limonciello, March 2007
# partially merged with startmythtv.sh by Michael Haas, October 2007
sleep 10
pidof mythfrontend.real 2>&1 >/dev/null && wmctrl -a "MythTV Frontend" 2>/dev/null && exit 0
```

This will cause the frontend startup to be delayed by 10 seconds, maybe you need only 5 or maybe 30 seconds. Save the file and reboot. Thats it.

Regards
Ian Dobson

---

### Post by gunsmoke on 2011-01-09
> **ian dobson said:**
> OK,

So you need to edit the following file:-  /usr/bin/mythfrontend
with your fav. text editor (I use nano from the terminal) and look for the line 

pidof mythfrontend.real 2>&1 >/dev/null && wmctrl -a "MythTV Frontend" 2>/dev/null && exit 0

now add a new line just before the pidof and add the following:
sleep 10

so the start of the file should look like:-

```
#!/bin/sh
# Mario Limonciello, March 2007
# partially merged with startmythtv.sh by Michael Haas, October 2007
sleep 10
pidof mythfrontend.real 2>&1 >/dev/null && wmctrl -a "MythTV Frontend" 2>/dev/null && exit 0
```

This will cause the frontend startup to be delayed by 10 seconds, maybe you need only 5 or maybe 30 seconds. Save the file and reboot. Thats it.


I used 5,10,30 second sleep, but same error after each restart.

Also when I try to watch television, I get this error:

> Error: MythTV is using all inputs, but there are no activer recordings

Can you say anyting more from this error?

---

### Post by newlinux on 2011-01-09
> **gunsmoke said:**
> Just installed latest Mythbuntu 10.10. + mythtv 0.24 (thru repository) After I have done the settings in the MythTV Backend setup, I get the following error message:



The set up is for a single unit BE/FE. IP adress is default 127.0.0.1.


I have installed Mythbuntu with the CD option, and also tried the option with installing mythubuntu ontop of a clean ubuntu 10.10 install, same error.


I have an other setup running ubunut 10.10 +Mythtv 0.23.1 working just fine.


Any sugestion how to resolve this issue?


> **gunsmoke said:**
> I used 5,10,30 second sleep, but same error after each restart.

Also when I try to watch television, I get this error:



Can you say anyting more from this error?

Does mythweb work on this machine? In the status page what does it report about the tuners? Do you have the proper IP address and password setup in mythfrontend? the front and back end logs might be useful.

---

### Post by Snelhest on 2011-01-09
I'm facing exactly the same issue.

Just tried to launch mythweb and it just gives an error message.

```
Error

Unable to connect to the master backend at 127.0.0.1:6543.
Is it running?
```

---

### Post by gunsmoke on 2011-01-10
> **newlinux said:**
> Does mythweb work on this machine? In the status page what does it report about the tuners? Do you have the proper IP address and password setup in mythfrontend? the front and back end logs might be useful.

I can see that mythweb is installed from the "Mythbuntu Control Center" and I understand that it's function is to remotly connect from another computer on the internett, but sadly I don't jet know how to use it...


but I was browsing my frontend and found the "System Status" and under Tuner Status, there where listed; "Tuner 3 has an error" under Details: 
[HTML]Tuner 3 [DVB:/dev/dvb/adapter0/frontend1] has an error[/HTML]

I have discovered earlier that the "frontend1" is the DVB-T tuner from my Hauppauge HVR4000. When trying to scan for channels on this tuner I get the following error:
> Timed out, no signal 
Signal Strength: 99%, signal/noise: 49%


Hope you can help, my head is boiling right know need a break:-k

---

### Post by gunsmoke on 2011-01-10
Ups! diden't answer all of your questions newlinux, here are some more info:

> **newlinux said:**
> Do you have the proper IP address and password setup in mythfrontend?
IP address: 127.0.0.1 both BE/FE Port 6543.

After running:
```
sudo cat /etc/mythtv/mysql.txt

```
I inserted the password from the output as explained in this howto [http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php")


> the front and back end logs might be useful.

I am not sure if these are what you looking fore:

> terje@ASUSM3N78:~$ tail -f /var/log/mythtv/mythbackend.log
2011-01-10 20:09:55.896 Enabled verbose msgs:  important general
2011-01-10 20:09:55.913 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-01-10 20:09:58.888 Reschedule requested for id -1.
2011-01-10 20:09:58.949 Scheduled 0 items in 0.1 = 0.01 match + 0.05 place
2011-01-10 20:09:58.963 Seem to be woken up by USER
2011-01-10 20:11:15.890 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-01-10 20:14:16.504 PID 0x280 status: Encrypted
2011-01-10 20:14:17.430 PID 0x200 status: Encrypted
2011-01-10 20:19:26.355 PID 0x284 status: Encrypted
2011-01-10 20:19:27.558 PID 0x201 status: Encrypted


> terje@ASUSM3N78:~$ tail -f /etc/init.d/mysql status
==> /etc/init.d/mysql <==
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the reload(8) utility, e.g. reload $JOB"
    reload "$JOB"
    ;;
*)
    $ECHO
    $ECHO "The script you are attempting to invoke has been converted to an Upstart" 1>&2
    $ECHO "job, but $COMMAND is not supported for Upstart jobs." 1>&2
    exit 1
esac
tail: kan ikke åpne «status» for lesing: Ingen slik fil eller filkatalog


Please give me the correct command, if you are missing anything from the logs.

Thanks

---

### Post by gunsmoke on 2011-01-16
Seems there is a missmatch between myth and hvr4000 dvb-t part.I found this forum article [http://www.mythtvtalk.com/hvr-4000-fails-scan-11318/]("http://www.mythtvtalk.com/hvr-4000-fails-scan-11318/")

Stating that there is a:
> Currently the kernel (2.6.32.2) has a problem with repeated open() and ioctl() of the HVR 4000 card.
I seems that it is an timing issue (thanks to Devin J. Heitmueller - Kernel Labs for the advise) with the DVB-T frontend (normally /dev/dvb/adapter0/frontend1). 

I tried to apply the hot fix to the 0.22 version, but failed at make...


But after I removed the frontend0 for the DVB-S part it resolved the > could not connect ot the master backend server error.

I will try to install from scratch agian, with this new info and leave out the DVB-S part, as I think it could be part of my trouble...:-k:-k

---

