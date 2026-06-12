---
title: "Likewise-open lsassd service won't start after reboot"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by jorge2904 on 2010-07-27
Im having an issue after I install likewise-open it works fine until i restart the machine the lsassd service won't start for any reason and it's status is dead. Any one run into this issue before?

---

### Post by rdrever on 2010-07-27
The same thing happened to me today on 2 machines after doing updates. I downgraded the likewise-open package to version 5.4.0.42111-2ubuntu1 from 5.4.0.42111-2ubuntu1.1 and everything is working properly now.

---

### Post by rallart888 on 2010-07-27
I am having the same problem hours ago too after updating and reboot, I am unable to logon using my AD username/password. I have googling all night trying to find a solution. So has anyone have a solution for this?

David.

---

### Post by transformania on 2010-07-27
I'm also having trouble after installing an update for Likewise-Open 5.4 (I'm on 10.04 x64) that came today via apt (07.27.10).

I tried uninstalling/purging/deleting then went for Likewise-Open 6.  6 works but has it's own problems.

Went back to 5.4, still can't start lsassd.

Going to try a fresh OS install on another machine tomorrow to try to determine if the problem is with the recent update or if I just botched my install to the point where I don't know how to fully un-install it and start over (I deleted everything I could find related to Likewise-Open before and after trying version 6).

---

### Post by rallart888 on 2010-07-28
> **transformania said:**
> I'm also having trouble after installing an update for Likewise-Open 5.4 (I'm on 10.04 x64) that came today via apt (07.27.10).

I tried uninstalling/purging/deleting then went for Likewise-Open 6.  6 works but has it's own problems.

Went back to 5.4, still can't start lsassd.

Going to try a fresh OS install on another machine tomorrow to try to determine if the problem is with the recent update or if I just botched my install to the point where I don't know how to fully un-install it and start over (I deleted everything I could find related to Likewise-Open before and after trying version 6).

I am using x64 as well.

I even tried uninstalling likewise and clean install, after install it works perfectlt I was able to join a domain. Then when I reboot, lsassd fails to start. So I tried manual start, it still fails!

---

### Post by SN8P on 2010-07-28
Same problem here with Ubuntu 10.04x64 /w likewise-open 5.4.0.42111-3~ppa7~lucid. 'lsassd' is marked as dead and failed to (re-)start, due to that a AD-login doesn't work.

```

# lwsm status lsass
dead
-or-
# /etc/init.d/lsassd status
dead

---8<---

# domainjoin-cli query
-after about 20sec-
Error: Unable to start daemon [code 0x00080018]

An attempt was made to start the '/etc/init.d/lsassd' daemon, but querying its status revealed that it
did not start. Try running '/etc/init.d/lsassd start; /etc/init.d/lsassd status' to diagnose the issue

```

---

### Post by gasparov on 2010-07-28
Add [this ppa]("https://launchpad.net/~likewise-open/+archive/ppa") and update

---

### Post by SN8P on 2010-07-28
> **gasparov said:**
> Add [this ppa]("https://launchpad.net/%7Elikewise-open/+archive/ppa") and update

I added it by using[INDENT][FONT=System]      add-apt-repository ppa:likewise-open/ppa[/FONT]
[FONT=System]    apt-get update
apt-get upgrade[/FONT]
[/INDENT]but nothing happens...

what are the differences compared to [Marc Gariepy's]("https://launchpad.net/%7Emgariepy/+archive/ppa?field.series_filter=lucid") version?

---

### Post by gasparov on 2010-07-28
> **SN8P said:**
> I added it by using[INDENT][FONT=System]      add-apt-repository ppa:likewise-open/ppa[/FONT]
[FONT=System]    apt-get update
apt-get upgrade[/FONT]
[/INDENT]but nothing happens...

what are the differences compared to [Marc Gariepy's]("https://launchpad.net/%7Emgariepy/+archive/ppa?field.series_filter=lucid") version?

Hi, are you sure that you don't have problems with the repository signature? 
You should find and upgrade to likewise-open-5.4.0.42111-2ubuntu1.2 as for [bug 610300]("https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/610300"). That should be a fix for the last update that broke things, I guess that in a short time it will be in the official tree.

Note that you will find the directory hierarchy of your home changed from /home/DOMAIN/user to /home/likewise-open/DOMAIN/user as per [bug 568422]("https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/568422")

P.S. try to use the force version feature of synaptic, package--> force version

---

### Post by SN8P on 2010-07-28
> **gasparov said:**
> Hi, are you sure that you don't have problems with the repository signature? 
You should find and upgrade to likewise-open-5.4.0.42111-2ubuntu1.2 as for [bug 610300]("https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/610300"). That should be a fix for the last update that broke things, I guess that in a short time it will be in the official tree.

Note that you will find the directory hierarchy of your home changed from /home/DOMAIN/user to /home/likewise-open/DOMAIN/user as per [bug 568422]("https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/568422")

P.S. try to use the force version feature of synaptic, package--> force version

```
# add-apt-repository ppa:likewise-open/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 1E7B2ECC0F647ECBBF204F9FE5D17263AAFDD5DB
gpg: Schlüssel AAFDD5DB von hkp Server keyserver.ubuntu.com anfordern
gpg: Schlüssel AAFDD5DB: Öffentlicher Schlüssel "Launchpad Likewise Open PPA" importiert
gpg: Anzahl insgesamt bearbeiteter Schlüssel: 1
gpg:               importiert: 1  (RSA: 1)
```

the output is german but it says that the pubkey has been imported which seems to acknowledged by the apt update command. well, the version numbers of yours and the one of Marc Gariepy looks quite similar!
[INDENT]5.4.0.42111-2ubuntu1.2  <=>  5.4.0.42111-3~ppa7~lucid
[/INDENT]but yours is *-2 and the other is *-3 so I guess the *newer* one - which isn't - is the 'mgariepy' one. I try again by purging the current lw version and removing the other repo.

---

### Post by SN8P on 2010-07-28
after all it seems to work but I have to add the domainname to the username even though I've set this in the registry!
[INDENT][FONT=System][HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory]
"AssumeDefaultDomain"=dword:00000001[/FONT]
[/INDENT]...so I guess some significant changes of Marc Gariepy are not in this version! what also is about cached credentials for more than 24 hours?!..

---

### Post by transformania on 2010-07-28
> **rallart888 said:**
> I am using x64 as well.

I even tried uninstalling likewise and clean install, after install it works perfectlt I was able to join a domain. Then when I reboot, lsassd fails to start. So I tried manual start, it still fails!

An update for my particular situation:  I have Likewise-Open 6 working for me, it seems.

The issue with it was that when I tried to open Firefox, it would give me that stupid "Firefox is already running..." rigmarole.  Deleting the lock file did not alleviate the problem.

Then I remembered that I was actually using the Firefox AppArmor profile.  I disabled that and now Firefox works.

Still no love with 5.4, but I'm going to follow the steps in this thread on another machine.  Thanks, everyone.

---

### Post by rallart888 on 2010-07-28
I have made changes to the home dir template to reflect my existing home folder %H/%D/%U which works fine if I login from the command line. If I tried logging in from the GUI my home dir is /home/likewise-open/domain/username.

How do I fix this?

---

### Post by SN8P on 2010-07-28
> **rallart888 said:**
> I have made changes to the home dir template to reflect my existing home folder %H/%D/%U which works fine if I login from the command line. If I tried logging in from the GUI my home dir is /home/likewise-open/domain/username.

How do I fix this?

since likewise changed to a registry you should use these command to change the home directory:
```

lwregshell set_value '[HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory]' HomeDirTemplate "<PATH>"
lwregshell set_value '[HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory\Pstore\Default\MachinePassword]' HomeDirTemplate "<PATH>"
lwregshell set_value '[HKEY_THIS_MACHINE\Services\lsass\Parameters\RPCServers\samr]' HomeDirTemplate "<PATH>"
lw-refresh-configuration
```either you use a shell script and exchange the <PATH> with a $variable or you change it by hand.
the default path in likewise is:[INDENT][FONT=System]/home/likewise-open/<DOMAIN>/<USER>
"%H/likewise-open/%D/%U"[/FONT]
[/INDENT]you always should start the path with %H 'cause it's the default linux home directory!
also you might use the reg-Editor '[FONT=System]lw-edit-reg[/FONT]'...

---

### Post by rallart888 on 2010-07-28
I made the changes through lw-edit-reg and it still pointing to /home/likewise-open/domain/username. 

Is there something else I need to change?

---

### Post by SN8P on 2010-07-28
'lw-refresh-configuration' should do the trick... if not try to reboot!
---8<---
...well, I think there is still a bug in the "official" version! the new settings registry is not properly processed. I switched to 'AssumeDefaultDomain=1' but it won't work!

---

### Post by gasparov on 2010-07-28
I didn't test it but maybe a symbolic link would do the job

---

### Post by rallart888 on 2010-07-28
> **gasparov said:**
> I didn't test it but maybe a symbolic link would do the job

I have created a symbolic link for now...

does anyone here know when will there be a fix?

---

### Post by SN8P on 2010-07-29
...there is still the question why registry values are not properly used?!
what is the problem? there is a 3rd-party version out there that fixed that befor the current issue!..
this is annoying! :-s

---

### Post by TonyFuller on 2012-09-26
Rather an old thread this but I have had fun with the latest upgrade to Ubuntu 10.04 LTS breaking the Ubuntu repository provided likewise-open where lsassd was not starting on boot, log on with a local account and you could start it ([FONT="Courier New"]sudo service lsassd start[/FONT]) okay, I had an Ubuntu machine that was okay and one that was not, the one that was okay has an [FONT="Courier New"]/etc/rc2.d/S21lsassd[/FONT] link to [FONT="Courier New"]../init.d/lsassd[/FONT], the machine that was not okay had [FONT="Courier New"]/etc/rc2.d/S01lsassd[/FONT] as its link in otherwords it was trying to start lsassd too soon, before other services it relied upon had been started.
The solution was:
1. Run "[FONT="Courier New"]who -r[/FONT]" to confirm the normal run level is 2.
2. Change to the appropriate /etc/rc?.d directory, i.e. in this case run: [FONT="Courier New"]cd /etc/rc2.d[/FONT]
3. As root move the link: [FONT="Courier New"]sudo mv S01lsassd S21lsassd[/FONT]

Reboot and all is well!

This referred to likewise-open 5.4.0.42111-2ubuntu1.3 in my case.

HTH

---

