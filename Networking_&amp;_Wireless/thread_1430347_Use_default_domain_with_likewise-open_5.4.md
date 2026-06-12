---
title: "Use default domain with likewise-open 5.4"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by Charlotte18 on 2010-03-15
In Likewise-open 5.4, something has changed, and the line "winbind use default domain = yes" can no longer be added to "/etc/samba/lwiauthd.conf" if you want the Ubuntu login screen to assume the default domain.

I found a thread that seems to offer a solution to this:

[http://www.mail-archive.com/likewise-open-discuss@lists.likewiseopen.org/msg00141.html](http://www.mail-archive.com/likewise-open-discuss@lists.likewiseopen.org/msg00141.html)

I do not understand the explanation given though. Does anyone know how to do this in 5.4?

---

### Post by Charlotte18 on 2010-03-15
After some investigation, I found that enabling the line "assume-default-domain = yes" in /etc/likewise/lsassd.conf works.

---

### Post by Charlotte18 on 2010-03-17
Okay, my last post does not in fact contain a solution for 5.4. Here's how I had to resolve this issue.

I completely removed 5.4, downloaded the 5.3 installer from likewise.com, joined the domain with that instead of with 5.4, and then enabled the line "assume-default-domain = yes" in /etc/likewise/lsassd.conf.  

I still cannot get 5.4 to work.

---

### Post by btmspox on 2010-03-25
There is an open bug for this: [https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/534629](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/534629)

---

### Post by Charlotte18 on 2010-04-14
Also, I should mention that using the version from likewise.com broke my local logins so that it was only possible to login via network accounts.  For me, since I had no network accounts with admin rights, this meant that I had to boot to terminal and edit the super user rights file in order to have any control over the system.  

None of this has been terribly inconvenient, but I hope likewise works correctly when 10.04 is finally released.

---

### Post by Charlotte18 on 2010-04-28
Does anyone know whether likewise-open 5.4 will allow the default login to be the domain, in the latest release of Ubuntu 10.04?  I cannot update my machines till this issue is fixed.

---

### Post by judomc on 2010-04-30
I tried it out today, upgrade from 9.10 with likewise-open 5 to 10.04 LTS/likewise-open 5.4 and default domain doesn't work.  It also didn't transfer my settings related to the restricted logins.  

It continues to treat usernames without the domain specified as unknown.

---

### Post by Charlotte18 on 2010-04-30
Did you try changing the line in lsassd.reg?

```
"AssumeDefaultDomain"=dword:00000000
``` 

to 

```
"AssumeDefaultDomain"=dword:00000001
``` 

You changed this, and it still doesn't work in the latest release?

---

### Post by estyles on 2010-05-05
Indeed, that does not work.  I changed the UseDefaultDomain settings, as well as the location to save user home directories (why the heck do they want to put "likewise-open" into the directory name?), and ran the command to update the "registry", with no luck.  Neither thing actually changed when I restarted.

Good to see that stuff in the LTS release actually has been tested to work... =P

---

### Post by Charlotte18 on 2010-05-07
At the bug report below, people are saying that the AssumeDefaultDomain setting works in package likewise-open_5.4.0.42111-3~ppa4~lucid_i386.deb.  My question is, where can I get likewise-open_5.4.0.42111-3~ppa4~lucid_i386.deb?

[https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/534629](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/534629)

EDIT: Nevermind. I seem to have found the package here:

[https://launchpad.net/~likewise-open/+archive/likewise-open-ppa/+build/1698123](https://launchpad.net/~likewise-open/+archive/likewise-open-ppa/+build/1698123)

I'm going to try it.

---

### Post by skyraven on 2010-05-17
Don't worry..
For me it still didn't work...(with what you said you were going to try)

Any solution for this issue ?

---

### Post by terazen on 2010-05-17
We're having the same problem.

---

### Post by skyraven on 2010-05-17
If you upgrade to this:
likewise-open_5.4.0.42111-3~ppa4~lucid_i386.deb
or the ppa5 build

then it works.
I've just solved it today...
[https://launchpad.net/~likewise-open/+archive/likewise-open-ppa?field.series_filter=lucid](https://launchpad.net/~likewise-open/+archive/likewise-open-ppa?field.series_filter=lucid)

take the repo from there and upgrade..it will fix the issue.

---

### Post by terazen on 2010-05-17
I had a problem with:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AAFDD5DB

Is that correct?  Also is the amd64 deb updated?

edit:
Using the amd64 version it's telling me I've joined the domain already and won't let me leave.  I could have swore I purged the package...

---

### Post by skyraven on 2010-05-18
Hmm can't give you any feedback here...
I'm on the intel side of things, not amd.

---

### Post by Charlotte18 on 2010-05-18
> **skyraven said:**
> Don't worry..
For me it still didn't work...(with what you said you were going to try)

Any solution for this issue ?

It is working.  First, to update to the new version of likewise, type the following commands in a terminal:


sudo add-apt-repository ppa:likewise-open/likewise-open-ppa

sudo aptitude update

sudo aptitude safe-upgrade

When this is done, you need to edit the /etc/likewise-open/lsassd.reg file. In the terminal type:

gksudo gedit /etc/likewise-open/lsassd.reg

When the file opens, change the line "AssumeDefaultDomain"=dword:00000000 to "AssumeDefaultDomain"=dword:00000001

Then go back to the terminal and type the following:

sudo lwregshell import /etc/likewise-open/lsassd.reg

sudo lw-refresh-configuration

Now, it should be working.

---

### Post by ilfernandes on 2010-05-18
yes it did work. thanks charllote18.

---

### Post by LebLinux on 2010-05-20
I updated the packages and srill could not login without typing the domain\user :(

I have installed (an update)

likewise-open 5.4.0.42111-3~ppa3~lucid
likewise-open-gui 5.4.0.42111-3~ppa3~lucid

And changed the value to 1 and yet did not work.


This is from /var/log/auth.log

May 20 13:51:43 irl000018569l gdm-session-worker[2678]: pam_succeed_if(gdm:auth): error retrieving information about user si22
May 20 13:51:47 irl000018569l gdm-session-worker[2678]: pam_unix(gdm:auth): check pass; user unknown
May 20 13:51:47 irl000018569l gdm-session-worker[2678]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=

---

### Post by Charlotte18 on 2010-05-20
> **LebLinux said:**
> 

And changed the value to 1 and yet did not work.After changing the value to 1, you must run the following commands in a terminal:

sudo lwregshell import /etc/likewise-open/lsassd.reg

sudo lw-refresh-configuration

---

### Post by LebLinux on 2010-05-20
> **Charlotte18 said:**
> After changing the value to 1, you must run the following commands in a terminal:

sudo lwregshell import /etc/likewise-open/lsassd.reg

sudo lw-refresh-configuration

I did and I even restarted the desktop. Nothing. I still have to use domain\username

---

### Post by Charlotte18 on 2010-05-20
You are not using the same likewise update as those who have the default domain login working.

The versions that are reported above to work are:

(1) likewise-open_5.4.0.42111-3~ppa4~lucid_i386.deb

(2) The package from the likewise-open-ppa repository: 5.4.0.42111-3~ppa5~lucid

---

### Post by LebLinux on 2010-05-20
Ohhh! I thought I downloaded the latest! could you provide me with the latest .deb package to download many thanks!

---

### Post by Charlotte18 on 2010-05-20
I updated by adding the ppa that I mentioned in a detailed post on page two:

[https://launchpad.net/~likewise-open/+archive/likewise-open-ppa?field.series_filter=lucid](https://launchpad.net/~likewise-open/+archive/likewise-open-ppa?field.series_filter=lucid)

I don't know where to download the deb directly.

---

### Post by LebLinux on 2010-05-20
Thank you it worked like a champ! :)

---

### Post by albertwt on 2010-12-08
> **LebLinux said:**
> Thank you it worked like a champ! :)

which one is working mate ?

I got the error like the following:

```
root@ISUZU:~# **add-apt-repository ppa:likewise-open/likewise-open-ppa**
Error reading https://launchpad.net/api/1.0/~likewise-open/+archive/likewise-open-ppa: <urlopen error [Errno 110] Connection timed out>

root@ISUZU:~#

```

---

### Post by atworkwithjf on 2011-01-14
You know that Likewise is shipping 6.0 now from their website.  [www.likewise.com/download](www.likewise.com/download)

This version is much farther ahead of the version in the distro, but it's still fully open-source.  Getting updates into packages in the main distro can be really slow so you might want to consider using the newest one on their site.

---

### Post by atworkwithjf on 2011-01-14
duplicate

---

### Post by linux.girl on 2012-02-08
Hello,

I am using likewise open version6.1.0.406 - and I still can't use a default domain to login, I always have to add yourdomain before username.

I don't have any of the files/directories mentioned here.

                 To complete the picture above, the procedure I used to install and add the computer to the domain is this one: [https://help.ubuntu.com/10.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/10.04/serverguide/C/likewise-open.html)
 But I am reading now on likewise.com several things that I should have that I simply dont. For example:
 the /opt is empty, there is no lwconfig there, no nothing, not even the domainjoin-gui.
 Everything is working fine, except I dont have any of these files  that I should have and therefore I cant even try to make the  assumedefaultdomainwork.
 Any ideas?

        
 
Thanks in advance,

linux.girl

---

### Post by Charlotte18 on 2012-02-08
The newest version of likewise has a checkbox that allows you to make the domain the default. You shouldn't need the instructions in this thread anymore.

[IMG]http://2.bp.blogspot.com/_j-wDivmP2lg/TSSLXISbRyI/AAAAAAAAAUg/gFcuNiE646c/s1600/fuduntu1477-1.png[/IMG]


Check the box and enter the proper prefix for your domain.

If you're not getting this checkbox by installing from the Ubuntu repository, try removing likewise and installing the version from beyondtrust.com

---

### Post by linux.girl on 2012-02-09
Hi there,

Thanks for the answer :-)

Yes, I did install it from the ubuntu repository and did not get a gui like the one you are showing.

I will try to follow your suggestion and let you know how it goes.

:-)

linux.girl

---

### Post by linux.girl on 2012-02-12
Hello, 

I tried to use the version from their official site (beyondtrust.com) just like you suggested, but unfortunately it did not work for me.

The problems:

1 - The gui below did not come up. So I still had to add the computer to the domain using the CLI.

2 - After the computer was added to the domain, I rebooted and the command prompt appeared just with a $, no hostname, no username. Using the up and down arrows to see previous commands also was not working. 

3 - since the gui didnt come up, I tried to change the lwconfig file, do assumedefaultdomain true. It did it, but after I logged in and out (and even reboot), I could no longer log into the computer with my account...

It gave me more problems than installing via cmd...so I dont know what to do now.

Any suggestions?

Thanks,

linux.girl

---

### Post by Charlotte18 on 2012-02-15
Did you remove the first likewise installation before you installed the one from beyondtrust.com? And how did you get from step 2 to step 3? 

If you're still unable to login via the Ubuntu gui, my advice is to unjoin from the domain using the terminal, then manually check /etc/hosts and /etc/hostname, removing any domain info there.  Then rebbot.

---

### Post by linux.girl on 2012-02-15
Hi Charlotte18,

I did the attempt on a different computer, one that never had likewise installed. It was a clean install.

On number 2, after a few reboots, the command prompt came back to normal and then I proceeded with the attempt to edit the  lwconfig file, do assumedefaultdomain true. It seemed it accepted the change, but once I logged out, I could no longer log in (with AD users - with local users I could log in).

When I got to that point, I decided I would try Centrify Express and see how it works. 

The issue with likewise is that when i installed it from the ubuntu repo, for some reason OPT folder was *empty* (I tried it many times on different hw). When installing from the website version, OPT seemed to contain all the correct files, but when I tried to edit when the files (lwconfig), it happened what I described above.


I am still evaluating both sw and eventually I will decide if to go with likewise or centrify.

thanks for your help!

linux.girl

---

