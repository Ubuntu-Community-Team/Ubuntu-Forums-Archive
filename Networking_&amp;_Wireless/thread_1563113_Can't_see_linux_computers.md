---
title: "Can't see linux computers"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by hawkdog on 2010-08-28
Hi

I am running Ubuntu 10.04 and I can see the Internet and windows computers on my network but I cannot see any Linux computers.  Any help is greatly appreciated.

Thanks

---

### Post by ex_isp on 2010-08-28
have you "shared" folders on the Linux machines you cant see?

---

### Post by hawkdog on 2010-08-28
yes folders are shared

---

### Post by ex_isp on 2010-08-28
Do you have firewalls enabled on these boxes that you can't see, and will they reply to a ping from local machine?

---

### Post by hawkdog on 2010-08-28
yes, I can ping other linux computer

---

### Post by ex_isp on 2010-08-28
Where is your share that you are trying to see mounted?  Somewhere in your home folder?

And when you shared this folder did it want to install sharing or samba service, or was it already installed?

And, Im assuming you are attempting to access this through the "my computer" icon...can you see yourself in there (provided you have a share on your main computer)?

---

### Post by ex_isp on 2010-08-28
Back in about 45...need to be outside spraying for ants/termites...but I think I can help you on this issue.

Ex

---

### Post by ex_isp on 2010-08-28
OK, back from spraying.

 #1  "Where is your share that you are trying to see mounted?  Somewhere in your home folder?

 #2  And when you shared this folder did it want to install sharing or samba service, or was it already installed?

 #3  And, Im assuming you are attempting to access this through the "my  computer" icon...can you see yourself in there (provided you have a  share on your main computer)?"

 #4  Just to be clear, Linux can see Win machines, but Win can't see Linux...correct?

---

### Post by hawkdog on 2010-08-28
windows can see linux. linux can see windows linux cannot see linux

---

### Post by ex_isp on 2010-08-28
Hawkdog, 
how many computers are we talking about?   really unusual in my experience that lin cant see lin but the other combos work...

---

### Post by ex_isp on 2010-08-28
in "computer" icon, can you completely NOT see the other Linux box, or can see but not access?

---

### Post by hawkdog on 2010-08-28
3.  1 running windows.  2 running linux.

---

### Post by ex_isp on 2010-08-28
> **ex_isp said:**
> in "computer" icon, can you completely NOT see the other Linux box, or can see but not access?

which of these is true?

---

### Post by hawkdog on 2010-08-28
under computer icon, then under network,  I see local computer and windows network,  under windows network I see MsHome and workgroup, under workgroup i see windows machine and local computer.  under mshome i get unable to mount location, failed to retrieve share list from server.

---

### Post by ex_isp on 2010-08-28
open terminal.

type:
sudo su
it will ask you for password and give you root

type:
net rap server domain

tell me if that shows your other linux box

---

### Post by hawkdog on 2010-08-28
it only shows windows pc and local machine

---

### Post by ex_isp on 2010-08-28
Wow!  I'm at a loss here.   I have 4 dif linux boxes on two workgroups and that command shows me everything in both groups...

Do I remember you saying they are in different groups?, or not?

---

### Post by hawkdog on 2010-08-28
same workgroup

---

### Post by ex_isp on 2010-08-28
I just pm'd Carlee, "long time user" to look at this thread.   I do not see why you are not even able to see tis other machine.   If that machine has a share on it, it should show up!

---

### Post by sandyd on 2010-08-28
set all your computers on your network to have a static IP (you can just do this in the router).

Then, run
```

sudo nano /etc/hosts

```enter in the static ip address of the computer followed by the name of the computer (there should already be some entries for you to use as an example).

Then, restart and try again.

If it still doesn't work, try browsing to 
smb:/<ip-address-of-computer-here>

---

### Post by ex_isp on 2010-08-28
Thanks for jumping in Carlee!

Ex

---

### Post by hawkdog on 2010-08-28
I am going to try the static approach also reconfigure everything.  i have gotten lost.

thank you for your time and patience

---

### Post by ex_isp on 2010-08-28
Please let know how it turns out!

ex

---

### Post by d3v1150m471c on 2010-08-28
you need samba. if your pings get a response it's probably not a connection problem. 
```

nmap -sP 192.168.0.1/24

```

---

### Post by ex_isp on 2010-08-28
He has Samba, as he CAN see his Linux shares from his Win machine...just not Lin to Lin

Ex

---

### Post by bodhi.zazen on 2010-08-28
> **carlee said:**
> set all your computers on your network to have a static IP (you can just do this in the router).

Then, run
```

sudo nano /etc/hosts

```enter in the static ip address of the computer followed by the name of the computer (there should already be some entries for you to use as an example).

Then, restart and try again.

If it still doesn't work, try browsing to 
smb:/<ip-address-of-computer-here>

I believe this may be the problem, you need to add an entry in /etc/hosts or run a local DNS server

For another example see :

[http://forums.virtualbox.org/viewtopic.php?f=1&t=15223#p64379](http://forums.virtualbox.org/viewtopic.php?f=1&t=15223#p64379)

---

### Post by d3v1150m471c on 2010-08-29
I had to modify my firewall to make my samba accessible. Allowing specific IP's or 192.168.1.0/24 to use the samba ports it should work. Make sure /etc/samba/smb.conf is set to share and your folder and contained files in that folder are shared. You can make them so by right clicking the containing folder and passing it to the contained files.

---

### Post by sandyd on 2010-08-29
> **bodhi.zazen said:**
> I believe this may be the problem, you need to add an entry in /etc/hosts or run a local DNS server

For another example see :

[http://forums.virtualbox.org/viewtopic.php?f=1&t=15223#p64379](http://forums.virtualbox.org/viewtopic.php?f=1&t=15223#p64379)

ive been meaning to ask a mod about this for a while now, (but I keep on forgetting). There seems to be extensive DNS issues, only with lucid. Ive already had to get 4 people to set external DNS nameservers (level 3, opendns, google) in order for them to resolve any addresses properly. any ideas about this? also, I dont think this is a linux issue, rather I think is a ubuntu issue. I had the same problem on one of my computers, and gentoo worked fine on it, without DNS issues.

---

### Post by Morbius1 on 2010-08-29
Maybe it's just me but there is a surprising lack of any real information to work with in this thread.

How does one of the Linux machines see the network's shares:
```
smbtree
```It may not have found anything either but you may have gotten error messages which might prove informative.

Is the firewall blocking access:
```
sudo nmap -sS -sU -T4 192.168.0.100
```If you change 192.168.0.100 to the ip address of the linux box you're currently running you would see if all the samba ports are open. Of course if they were closed Windows wouldn't get access either.

We are all making the assumption that he's using Samba but we really don't know that. He could be using "Simple File Sharing" which has nothing to do with Samba. And if he were using Samba to share folders which method of samba is he using:
```
net usershare info
``````
testparm -s
```This would tell us if he's using samba, what method of samba, and how his shares are configured.

At the moment we seem to be focusing on name resolution ( host file, etc..). But you have to wonder how the Windows box is making this resolution and not the Linux boxes. I'm not saying it's not the answer I just don't have any information to suggest it is.

I don't have any answers because there is no information to form an opinion so just consider this comic relief. :wink:

---

### Post by bodhi.zazen on 2010-08-29
> **carlee said:**
> ive been meaning to ask a mod about this for a while now, (but I keep on forgetting). There seems to be extensive DNS issues, only with lucid. Ive already had to get 4 people to set external DNS nameservers (level 3, opendns, google) in order for them to resolve any addresses properly. any ideas about this? also, I dont think this is a linux issue, rather I think is a ubuntu issue. I had the same problem on one of my computers, and gentoo worked fine on it, without DNS issues.

I do not know for sure as I do not use nautilus much, and even less for browsing network (samba) shares.

There are numerous bug reports in launchpad, but I did not find an answer or a solution.

Basically, you can mount samba shares via the command line (I use either the command line or autofs), but nautilus will not show the share graphically. Sometimes it seems nautilus will not give an opportunity to enter a user name and/or password.

The solution (for some) seems to be one of the following:

1. Add an entry into fstab.

2. Use autofs (I like autofs).

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

3. Add a dns server (dnsmask), winbind, or an entry in /etc/hosts.

I will look at nautilus in the next few days and provide more information if I can. From the bug reports people seem to indicate they feel the problem is "upstream" and since I see the same behavior in Fedora and Ubuntu they may be correct.

Because the underlining command line tools work, I suspect a problem with nautilus.

Here are two bug reports :

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/193232](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/193232)

There are others if you search ...

As far as additional information, see the wiki:

[https://wiki.edubuntu.org/DebuggingSamba](https://wiki.edubuntu.org/DebuggingSamba)

---

### Post by sandyd on 2010-08-29
> **bodhi.zazen said:**
> I do not know for sure as I do not use nautilus much, and even less for browsing network (samba) shares.

There are numerous bug reports in launchpad, but I did not find an answer or a solution.

Basically, you can mount samba shares via the command line (I use either the command line or autofs), but nautilus will not show the share graphically. Sometimes it seems nautilus will not give an opportunity to enter a user name and/or password.

The solution (for some) seems to be one of the following:

1. Add an entry into fstab.

2. Use autofs (I like autofs).

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

3. Add a dns server (dnsmask), winbind, or an entry in /etc/hosts.

I will look at nautilus in the next few days and provide more information if I can. From the bug reports people seem to indicate they feel the problem is "upstream" and since I see the same behavior in Fedora and Ubuntu they may be correct.

Because the underlining command line tools work, I suspect a problem with nautilus.

Here are two bug reports :

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/193232](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/193232)

There are others if you search ...

As far as additional information, see the wiki:

[https://wiki.edubuntu.org/DebuggingSamba](https://wiki.edubuntu.org/DebuggingSamba)
Since I have gentoo, im going to be doing some tests with the various versions of nautilus (from git and release) ... perhaps I can find a version that works, and get it compiled for lucid in a ppa or something.
------------------------------------------------
DONE.
@OP install the "samba" package. and try. If youve already installed it, ignore me..

@bodhi.zazen Unless this bug is NOT related to nautilus, or in some part created by modifications done by the ubuntu packagers, Nautilus 2.30.1 (straight from source) is working fine. (except that there were a few patches, check below).

Additionally, this may be because the router may only be an DNS fowarder, which creates the problem that you described, as windows machines normally run their own DNS.

however, winbind itself is one of the requirements of the samba metapackage -> [http://packages.debian.org/lenny/samba](http://packages.debian.org/lenny/samba) so these problems should not be hapenning.
EDIT: nvm. ubuntu apparently only installs the samba package, but not he meta.
```

[COLOR=Black]sandy@sandyd-laptop /mnt/BACKUP $ sudo emerge -av nautilus

[/COLOR][COLOR=Black]* IMPORTANT: 5 news items need reading for repository 'gentoo'.
 [/COLOR][COLOR=Black]* Use eselect news to read news items.


These are the packages that would be merged, in order:[/COLOR][COLOR=Black]

Calculating dependencies... done![/COLOR]     [COLOR=Black]
[ebuild   R   ] gnome-base/nautilus-2.30.1-r1  USE="gnome -doc -test -xmp" 0 kB

Total: 1 package (1 reinstall), Size of downloads: 0 kB[/COLOR] [COLOR=Black]

Would you like to merge these packages? [[/COLOR] [COLOR=Black]Yes/[/COLOR][COLOR=Black]No] YES

>>> Verifying ebuild manifests[/COLOR] [COLOR=Black]

>>> Emerging (1 of 1) gnome-base/nautilus-2.30.1-r1[/COLOR] [COLOR=Black]
 * nautilus-2.30.1.tar.bz2 RMD160 SHA1 SHA256 size ;-) ...                      [ ok ]
 * checking ebuild checksums ;-) ...                                            [ ok ]
 * checking auxfile checksums ;-) ...                                           [ ok ]
 * checking miscfile checksums ;-) ...                                          [ ok ]
 * CPV:  gnome-base/nautilus-2.30.1-r1
 * REPO: gentoo
 * USE:  amd64 elibc_glibc gnome kernel_linux multilib userland_GNU
>>> Unpacking source...
>>> Unpacking nautilus-2.30.1.tar.bz2 to /var/tmp/portage/gnome-base/nautilus-2.30.1-r1/work
>>> Source unpacked in /var/tmp/portage/gnome-base/nautilus-2.30.1-r1/work
>>> Preparing source in /var/tmp/portage/gnome-base/nautilus-2.30.1-r1/work/nautilus-2.30.1 ...
 * Fixing OMF Makefiles ...                                                      [ ok ]
 * Running elibtoolize in: nautilus-2.30.1/
[B] *   Applying portage-2.2.patch ...
 *   Applying sed-1.5.6.patch ...
 *   Applying as-needed-2.2.6.patch ...
 * Applying nautilus-2.27.4-change-reg-desktop-file-with-no-desktop.patch ...    [ ok ]
 * Applying nautilus-2.30.1-unmount-entries.patch ..[/B][/COLOR] [COLOR=Black].                            [ ok ]
>>> Source prepared.[/COLOR]

```

---

### Post by sandyd on 2010-08-29
> **bodhi.zazen said:**
> I do not know for sure as I do not use nautilus much, and even less for browsing network (samba) shares.

There are numerous bug reports in launchpad, but I did not find an answer or a solution.

Basically, you can mount samba shares via the command line (I use either the command line or autofs), but nautilus will not show the share graphically. Sometimes it seems nautilus will not give an opportunity to enter a user name and/or password.

The solution (for some) seems to be one of the following:

1. Add an entry into fstab.

2. Use autofs (I like autofs).

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

3. Add a dns server (dnsmask), winbind, or an entry in /etc/hosts.

I will look at nautilus in the next few days and provide more information if I can. From the bug reports people seem to indicate they feel the problem is "upstream" and since I see the same behavior in Fedora and Ubuntu they may be correct.

Because the underlining command line tools work, I suspect a problem with nautilus.

Here are two bug reports :

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/193232](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/193232)

There are others if you search ...

As far as additional information, see the wiki:

[https://wiki.edubuntu.org/DebuggingSamba](https://wiki.edubuntu.org/DebuggingSamba)
I meant that some linux users are having total issues resolving ANY address or having intermettient issue, not only the ones on their local net.

I fixed those issues with the fix mentioned at -> [https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757)

which resolved the outside DNS issues, but in the end, the users still had to grab winbind, or add the local addresses to their hosts file in order to resolve local addresses.

Ive already gotten
[http://ubuntuforums.org/showthread.php?p=9704793#post9704793](http://ubuntuforums.org/showthread.php?p=9704793#post9704793)
and [http://ubuntuforums.org/showthread.php?p=9753411#post9753411](http://ubuntuforums.org/showthread.php?p=9753411#post9753411)
and [https://answers.launchpad.net/ubuntu/+source/apt/+question/117265](https://answers.launchpad.net/ubuntu/+source/apt/+question/117265) 

Since DNS is normally set to be resolved from the router, I be
(ive contacted the poster a few minutes ago, and am currently waiting for a reply..)

oh, and this is seperate from the problem at hand. move if necessary

---

### Post by redmk2 on 2010-08-29
> **carlee said:**
> I meant that some linux users are having total issues resolving ANY address, not only the ones on their local net.

I fixed those issues with the fix mentioned at -> [https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757)

which resolved the outside DNS issues, but in the end, the users still had to grab winbind, or add the local addresses to their hosts file in order to resolve local addresses.

Can you explain how **winbind **resolves local DNS issues.  I always thought of **winbind **as a set of routines to map Windows users to Linux users, in: "Winbind maintains a database called winbind_idmap.tdb in which it stores mappings between UNIX UIDs, GIDs, and NT SIDs".  See [**_here_**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html").

I believe you will find that Samba ultimately uses NetBIOS to resolve SMB resources.  [**_This thread _**]("http://ubuntuforums.org/showthread.php?t=1471622&page=3")covers it pretty well.

I for one would like to know why this problem (no browse lists) happens more in Lucid (10.04) that in earlier releases.  Is there a FW setting that has changed?  It sure seems that most of these problems turn out to be due to faulty (or no) DNS or firewall settings that restrict NetBIOS broadcasts.  Firestarter has been at fault with blocking ports in the past. 

I don't have 10.04 LTS installed for just this reason.  

I have 8.04 installed with local DNS resolution.  I don't have WINS server.  Everything works great.  Browsing via Nautilus works perfectly. I do not have any problems with ad hoc users shares appearing on the network.  These can be either Samba or Windows including Vista and Win7.

So I guess the question I would most like to see answered is: What is the root problem to Samba name resolution for browsing?  Is it lack of name resolution?  Or is it a default firewall (UFW) setting that restricts TCP and UDP ports (137/138/139 and 445)?  Or is it something else.

---

### Post by sandyd on 2010-08-29
> **redmk2 said:**
> Can you explain how **winbind **resolves local DNS issues.  I always thought of **winbind **as a set of routines to map Windows users to Linux users, in: "Winbind maintains a database called winbind_idmap.tdb in which it stores mappings between UNIX UIDs, GIDs, and NT SIDs".  See [**_here_**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html").
[B]WINBIND itself is a domain resolver. see -> [http://packages.debian.org/lenny/winbind](http://packages.debian.org/lenny/winbind)

Since WINBIND can resolve the addresses, there is no reason to need to add them to the HOSTS file.
[/B] 
I believe you will find that Samba ultimately uses NetBIOS to resolve SMB resources.  [**_This thread _**]("http://ubuntuforums.org/showthread.php?t=1471622&page=3")covers it pretty well.

I for one would like to know why this problem (no browse lists) happens more in Lucid (10.04) that in earlier releases.  Is there a FW setting that has changed?  It sure seems that most of these problems turn out to be due to faulty (or no) DNS or firewall settings that restrict NetBIOS broadcasts.  Firestarter has been at fault with blocking ports in the past. 
**Whats your network config? im curious. (model of router, .etc .etc). Im asking this to narrow down the issues, because this issue can possibly simply be because of the fact that your router fowards DNS requests. In that case, then WINBIND is a okay fix.**
I don't have 10.04 LTS installed for just this reason.  

I have 8.04 installed with local DNS resolution.  I don't have WINS server.  Everything works great.  Browsing via Nautilus works perfectly. I do not have any problems with ad hoc users shares appearing on the network.  These can be either Samba or Windows including Vista and Win7.

So I guess the question I would most like to see answered is: What is the root problem to Samba name resolution for browsing?  Is it lack of name resolution?  Or is it a default firewall (UFW) setting that restricts TCP and UDP ports (137/138/139 and 445)?  Or is it something else.
ive currently sent messages to users who have had this issue. And yes, there are currently a lot. As stated above in my post, it seems to be an issue with the ubuntu configuration, because a system that is built compltetly from source does not have this issue. (and using quite unstable new packages as well)

---

### Post by redmk2 on 2010-08-30
> **carlee said:**
> ive currently sent messages to users who have had this issue. And yes, there are currently a lot. As stated above in my post, it seems to be an issue with the ubuntu configuration, because a system that is built compltetly from source does not have this issue. (and using quite unstable new packages as well)

So I'll ask you again: What does **[COLOR="Red"]winbind  [/COLOR]** have to do with it?

What do you think is the root problem in either configuration or in the installation?

My systems have used only packages.  I have both a Desktop and a Server.  The only thing that configures the ***smbd daemon *** is the smb.conf file.  What could possibly be different between installing from source or using the package?

---

### Post by sandyd on 2010-08-30
> **redmk2 said:**
> So I'll ask you again: What does **[COLOR="Red"]winbind  [/COLOR]** have to do with it?

What do you think is the root problem in either configuration or in the installation?

My systems have used only packages.  I have both a Desktop and a Server.  The only thing that configures the ***smbd daemon *** is the smb.conf file.  What could possibly be different between installing from source or using the package?

check the bolded text for winbind (the post before the one you just quoted). the difference between installing from source and using the package is that there are very very little modification to the source code when installing. This checks the possibility that a modification done by the ubuntu devs is causing this. Ill hopefully get some time to look through all this stuff tomorow and fetch my old DL-604 router out of the basement to see if this is a forwarding problem after all (my current setup uses internal dns, so I have to use the DL-604 in order to test)

---

### Post by redmk2 on 2010-08-30
Sorry, I did not see it buried in you original quote.

> WINBIND itself is a domain resolver. see -> [http://packages.debian.org/lenny/winbind]("http://packages.debian.org/lenny/winbind")

Since WINBIND can resolve the addresses, there is no reason to need to add them to the HOSTS file.

I don't see where it states that in above URL you listed.    

All I see is this:> [B][SIZE="3"]Package: winbind (2:3.2.5-4lenny12) [security]
service to resolve user and group information from Windows NT servers
[/SIZE][/B]
This package provides the winbindd daemon, which provides a service for the Name Service Switch capability that is present in most modern C libraries (like the GNU C Library - glibc.)

The service provided by winbindd is called `winbind' and **can be used to resolve user and group information from a Windows NT server. **The service can also provide authentication services via an associated PAM module.

What am I missing here?

> Whats your network config? im curious. (model of router, .etc .etc). Im asking this to narrow down the issues, because this issue can possibly simply be because of the fact that your router fowards DNS requests. In that case, then WINBIND is a okay fix.
 
What issues do you think I have?  My network functions correctly.  I can browse the shares in Nautilus.  I can see the shares from the command line.  I can see ad hoc user shares come and go when friends attach to the network.  My concern is in updating Ubuntu, not my current setup.  I'm in no hurry, I would rather work out the real root cause.  I am interested in solving this.  How can I help you with this?
 
The router is a 4 year old Westell residential gateway.  This supplies DNS and DHCP.  It does not forward any requests for LAN name resolution.  The LAN is NAT'd behind a Verizon supplied WAN address.  All the desktop and server hosts have statically configured IP addresses.  There is a wireless AP to facilitate the laptops that have dynamically supplied IP's.  The DHCP pool is limited to 10 addresses by my configuration.  There is nothing special about the network at all.  It has accommodated all windows clients from W2K to Win7 and all Ubuntu from 7.04 on.

[COLOR="Purple"]**Edit:**  I think that you are right that this is a Ubuntu problem.  I just don't think it is a Samba package problem.   I think it's more in the basic distro configuration.  Maybe UFW.  Maybe the default DNS resolution.  Another thought might be the way Upstart starts the processes.  10.04 is the first time Samba has been started by Upstart. 

Don't use Gentoo to compare the install with. Gentoo has to many differences in functionality.  The most  obvious is in the init system:  SysV vs. Upstart and the use of UFW  on Ubuntu.[/COLOR]

---

### Post by bodhi.zazen on 2010-08-30
Thank you for the information carlee.

I am not certain of the source of the problem, but I can confirm nautilus does not see the ubuntu share (Fedora client, Ubuntu server) unless I add an entry into /etc/hosts (on Fedora for the Ubuntu server), then I can see and mount the share.

---

### Post by redmk2 on 2010-08-30
> **bodhi.zazen said:**
> ...
I am not certain of the source of the problem, but I can confirm nautilus does not see the ubuntu share (Fedora client, Ubuntu server) unless I add an entry into /etc/hosts (on Fedora for the Ubuntu server), then I can see and mount the share.

Samba uses the DNS name (hostname) to convert to a NetBIOS name.  Without that the browse master can't create a list of SMB resources (shares).  This does not stop you from directly requesting the share by IP address.  Nautilus should be able to handle the request by IP.

---

### Post by sandyd on 2010-08-30
> **redmk2 said:**
> Sorry, I did not see it buried in you original quote.



<snip>
> **can be used to resolve user and group information from a Windows NT server**

Which is the reason why winbind resolves local addresses. And sorry, but I need to go into a bit about how windows servers work here, so hang on....

All of the computers on a windows network (with a windows server) all have an record on the actual server, with the local IP address with the server, and the NETBIOS name of the server. Due to the fact that the server needs to know which computer the user is logged into, for security and authentication reasons, they need to match the user to the computer. Since windows computers already have a resolver, they can easily accomplish this. 

However, in order to log in properly, and act as a Primary or Secondary Domain Server, or as some kind of authentication server, Linux computers MUST have their own resolver (just as Windows users have their own) (which by default, Linux doesn't) so that they can tell who is logged into where. The above statement shows that it is used to retrieve user and group info from a windows NT server. In order to do this, the computer is required to have a local domain resolver. Winbind  provides that functionality on the side.

---

### Post by sandyd on 2010-08-30
> **redmk2 said:**
> Samba uses the DNS name (hostname) to convert to a NetBIOS name.  Without that the browse master can't create a list of SMB resources (shares).  This does not stop you from directly requesting the share by IP address.  Nautilus should be able to handle the request by IP.
and Nautilus can't.
and neither can konqueror.

They seem to need the address to be resolved before allowing the share to show up.

---

### Post by Morbius1 on 2010-08-30
I was wondering how long it would take before someone brought up winbind. I'm not going to get into the debate about winbind. It's will be as frustrating as arguing that all workgroup names don't have to match and all the usernames and passwords don't have to be exactly the same on all machines on the network.

This thread has turned into a private conversation between two members and that's fine but for those playing the home version of this game I would like to restate the original post:
> I am running Ubuntu 10.04 and I can see the Internet and windows computers on my network but I cannot see any Linux computersWe really don't know what the original poster has done to his machines because no one has asked him but assuming if it's a plain out of the box install it does appear that he can access his windows box by name. Presumably without winbind, hosts, or even lmhosts being configured.

---

### Post by hawkdog on 2010-08-30
It has occurred to me that my setup may be the problem.  I have 4 computers; one running windows 7, one desktop running Ubuntu only,  the other two are laptops on which I installed Ubuntu using WUBI.  It is  my understanding that WUBI is a windows program that runs Ubuntu in a virtual environment,  Therefore, is it possible that something in WUBI is causing my problem?

---

### Post by Morbius1 on 2010-08-30
Do you have shares defined on the Ubuntu desktop?

If so would you mind posting the output of the following commands:
```
smbtree
``````
net usershare info
``````
testparm -s
```Aslo, and this really should have been step 1, is nmbd running:
```
sudo service nmbd status
```If it's not running, start it:
```
sudo service nmbd start
```Even if you don't have any shares on the desktop run the smbtree and nmbd check anyway.

---

### Post by nhoward on 2010-08-30
-hawkdog: I doubt it because I am having the same problem and I am using two native 10.04 machines, and I cannot get my laptop to see my desktop shared files. I have read the whole thread and none of the suggestions have worked for me either.

---

### Post by redmk2 on 2010-08-30
> **carlee said:**
> Which is the reason why winbind resolves local addresses. And sorry, but I need to go into a bit about how windows servers work here, so hang on....

All of the computers on a windows network (with a windows server) all have an record on the actual server, with the local IP address with the server, and the NETBIOS name of the server.Sort of...  **All the hosts** on a network using NetBIOS name resolution maintain a cache of **all NtBIOS name mappings.  See [[B]_here_**]("http://articles.techrepublic.com.com/5100-10878_11-5034239.html")[/B].>  

Due to the fact that the server needs to know which computer the user is logged into, for security and authentication reasons, they need to match the user to the computer. Since windows computers already have a resolver, they can easily accomplish this.
NetBIOS is for COMPUTER/MACHINE name to IP address name resolution.  There is user no authentication involved at all.> 

However, in order to log in properly, and act as a Primary or Secondary Domain Server, or as some kind of authentication server, Linux computers MUST have their own resolver (just as Windows users have their own) (which by default, Linux doesn't) so that they can tell who is logged into where. The above statement shows that it is used to retrieve user and group info from a windows NT server. In order to do this, the computer is required to have a local domain resolver. Winbind  provides that functionality on the side.
I'm not sure we are even talking about the same processes.  NetBIOS is not Samba.  Samba is really a suite of protocols.  It maintains it's own security database for user authentication.  Could you be referring to the WINS database.  

The WINS database only holds IP addresses, COMPUTER names and MAC addresses.  WINS is not needed in a single subnet LAN.  Its value is when you have multiple subnets that need to NetBIOS COMPUTER name to IP resolution.

---

### Post by redmk2 on 2010-08-30
> **nhoward said:**
> -hawkdog: I doubt it because I am having the same problem and I am using two native 10.04 machines, and I cannot get my laptop to see my desktop shared files. I have read the whole thread and none of the suggestions have worked for me either.

WUBI can add to the list of problems.

@hawkdog and nhoward

Can you ping by ***hostname*** between the Linux hosts?

What are the results of the tests Morbius1 suggested?

---

### Post by hawkdog on 2010-08-30
bill@bill-desktop:~$ smbtree
Enter bill's password: 
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
WORKGROUP
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
cli_start_connection: failed to connect to UBUNTU<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
MSHOME
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
bill@bill-desktop:~$ net usershare info
[documents]
path=/home/bill/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

[pictures]
path=/home/bill/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[software]
path=/home/bill/Desktop/Software
comment=
usershare_acl=Everyone:R,
guest_ok=y

info_fn: file /var/lib/samba/usershares/presario is not a well formed usershare file.
info_fn: Error was Path is not a directory.
bill@bill-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[cups]"
NOTE: Service cups is flagged unavailable.
Processing section "[bill linux]"
Processing section "[File System]"
Processing section "[Desktop]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = bill
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[cups]
	comment = Printer Drivers
	path = /etc/cups
	read only = No
	available = No

[bill linux]
	path = /home/bill
	read only = No

[File System]
	path = /

[Desktop]
	path = /home/bill/Desktop
	read only = No
bill@bill-desktop:~$ sudo service nmbd status
nmbd start/running, process 1035
bill@bill-desktop:~$

---

### Post by Morbius1 on 2010-08-30
You've got a bit of a mess there on your Ubuntu box.

You're using security = SHARE instead of the default.

You've forced the guest account to = your own user name.

You're attempting to share your home directory ( not a good idea ) and are a requesting authentication ( a slightly better idea ). But did you create a smbpasswd and samba users for this access?

And you're attempting to do this:
> [File System]
    path = /

[Desktop]
    path = /home/bill/Desktop
    read only = NoThere's a System Administrator somewhere that just seized up.

I don't know if the better idea would be to reset your self to the default smb.conf and start over - relatively easy to do - or try to fix this thing.


There's an easy fix for the lanman error but I'm having a hard time following what remote box is requesting the lanman authentication.

Anyway to fix the lanman thing:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following lines in the [global] section of /etc/samba/smb.conf :
```
client lanman auth = Yes 
lanman auth = Yes 
```Save the file, exit gedit, and back in the terminal type:
```
sudo service smbd restart
```

---

### Post by Morbius1 on 2010-08-30
But there's more. You have a Nautilus-share ( usershare ):
> [software]
path=/home/bill/Desktop/Software
comment=
usershare_acl=Everyone:R,
guest_ok=yWithin a Classic-share:
> [Desktop]
    path = /home/bill/Desktop
    read only = NoThe resulting access of that is completely up to the remote user.

If an anonymous remote user accesses the software share he will gain access without gaining access to the Desktop share itself. If an authenticated user accesses the Desktop share first he will have write access to the child "software" share which you are trying to prevent.

The moral of this is never create shares within shares.

Another moral is never use Nautilus-share and Classic-share at the same time. It's easy to get confused over what you have already shared.

You need to decide which one you want.

---

### Post by bodhi.zazen on 2010-08-30
> **redmk2 said:**
> Samba uses the DNS name (hostname) to convert to a NetBIOS name.  Without that the browse master can't create a list of SMB resources (shares).  This does not stop you from directly requesting the share by IP address.  Nautilus should be able to handle the request by IP.

Umm ...

That is the whole point of what I have been saying.

The OP, and many others, expect to be able to browse samba shares graphically with nautilus. If you read my posts, I understand you can mount the samba share via other techniques, command line or entering the share manually.

The OP wants to do this graphically. My advice is to add a dns server or add an entry in /etc/hosts, both of which allow graphical browsing of shares, which is what the OP is asking.

Do you have a better solution ?

---

### Post by redmk2 on 2010-08-30
> **bodhi.zazen said:**
> Umm ...

That is the whole point of what I have been saying.

The OP, and many others, expect to be able to browse samba shares graphically with nautilus. If you read my posts, I understand you can mount the samba share via other techniques, command line or entering the share manually.

The OP wants to do this graphically. My advice is to add a dns server or add an entry in /etc/hosts, both of which allow graphical browsing of shares, which is what the OP is asking.

Do you have a better solution ?

The intent of my response was to (gently) eliminate the part about Winbind.  Winbind has nothing to do with NetBIOS resolution.  I find it hard to understand why this issue keeps coming up.

One more time if I may: NetBIOS is not WINS nor is it Winbind.  Although NetBIOS is needed, WINS is optional and Winbind is irrelevant.

The solution for "browsing shares" shares is pretty basic.  The user has to have some name service on the network. This implies that TCP/UDP ports 137/138/139 and 445 be available, as NetBIOS  is always used in the end.  

Apparently he default firewall (UFW) does not allow these ports to be open with the initial install.

It is only my opinion that along with all the general misconfiguration that seems to go on, there is 2 basic problems 
[LIST=1]
[*]The default UFW install. You need to add **nf_conntrack_netbios_ns **to the IPT MODULES or turn off UFW
[*]Not using LOCAL name services
[/LIST]

One last thought about UFW.  I don't use any firewalls on my local LAN.  I do run a firewall at the gateway.  No Samba traffic  crosses the gateway.  I understand the need for UFW for single host Internet use, but if a user is going to have multiple hosts it is more efficient to place the firewall at the edge of the network.  
.

---

### Post by hawkdog on 2010-08-30
Sorry, but I am a novice to linux and I am totally confused.

---

### Post by Morbius1 on 2010-08-30
> **bodhi.zazen said:**
> The OP wants to do this graphically. My advice is to add a dns server or add an entry in /etc/hosts, both of which allow graphical browsing of shares, which is what the OP is asking.

Do you have a better solution ?
He already can browse the shares graphically - the Windows shares. And he's able to do that with the only mechanism that works by default in linux - bcast. No winbind, no WINS server, no hosts file, and no lmhosts file.

The problem is he can't access any Linux shares. Right now , at least on one Ubuntu machine, his smb.conf and shares are messed up. It's going to take an iterative process to clean that up unless he wants to start over. He also has two specific errors from smbtree:

> Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIEDWe can fix the lanman error I think.
> \\UBUNTU                 ubuntu server (Samba, Ubuntu)
cli_start_connection: failed to connect to UBUNTU<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSEDYou'll note that smbtree can see the machine by name but is refused access. Why? A bad smb.conf? A firewall? We don't know yet.

---

### Post by redmk2 on 2010-08-30
> **Morbius1 said:**
> He already can browse the shares graphically - the Windows shares. And he's able to do that with the only mechanism that works by default in linux - bcast. No winbind, no WINS server, no hosts file, and no lmhosts file.

You need an /etc/hosts file for the host itself to know its own name/IP mapping.  Then it can b'cast its NetBIOS name.  There is no need to have all the hostnames in the network in the file.

---

### Post by Morbius1 on 2010-08-30
Before I get sucked into this side argument more than I already have I would like to offer the following up to a vote by the others on this thread.

We have to many unknowns at this point so I would suggest resetting samba on the one machine to the factory settings and creating one simple nautilus-share so restart our journey:

If you're interested here's a procedure to start from scratch:

**(1) Make sure the following file exists: **
/usr/share/samba/smb.conf

**(2) Make a backup of your current smb.conf**
```
      sudo cp /etc/samba/smb.conf /etc/samba/smb.confMOD 
```**(3) Start with a fresh one:**
```
       sudo cp -a /usr/share/samba/smb.conf /etc/samba/ 
```**(4) Correct one mistake in the new one:**
Find the line:
>   encrypt passwords = false                                 and change it to:
>       encrypt passwords = true                                 **(5) Restart samba**
```
      sudo service smbd restart 
```**(6) Use Samba Nautilus-share to create a guest share:**

Open Nautilus
Right click on /home/your_user_name/Documents
Select "Sharing Options"
Select "Share this Folder", "Allow others to create and delete..", and "Guest access"
Select "Create Share"

It will ask you if you want it to modify permissions - you do.

> [COLOR=Blue]**redmk2,**[/COLOR] You need an /etc/hosts file for the host itself to know its own  name/IP mapping.  Then it can b'cast its NetBIOS name.  There is no need  to have all the hostnames in the network in the file.Quite right, this thread is driving me crazy,  and well, you know.....:oops:

---

### Post by Morbius1 on 2010-08-30
Democracy is highly overrated. 

hawkdog, Go for it.

We need to eliminate samba and it's shares as a possible source of the problem. Reseting to the factory settings will do that. 

Once you're done, post the output of the following commands so we can all verify that samba is OK:
```
net usershare info
``````
testparm -s
```

---

### Post by hawkdog on 2010-08-30
Okay I did what you asked and here are the results


bill@bill-desktop:~$ net usershare info
[documents]
path=/home/bill/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

[pictures]
path=/home/bill/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[software]
path=/home/bill/Desktop/Software
comment=
usershare_acl=Everyone:R,
guest_ok=y

info_fn: file /var/lib/samba/usershares/presario is not a well formed usershare file.
info_fn: Error was Path is not a directory.
bill@bill-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

---

### Post by Morbius1 on 2010-08-31
OK, that looks like the standard smb.conf. You only have one error in your Nautilus-shares but it looks like it's referencing a path that does not exist so samba will just ignore it which is OK.

Now let's take a look at the firewall issue that [COLOR=Red]**redmk2**[/COLOR] brought up:

**1st: install nmap:**
```
sudo apt-get install nmap
```**2nd: In a terminal from this same box issue the following command:**
```
 sudo nmap -sS -sU -T4 192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to your own ip address on that box.*[/COLOR] 

If you don't know what the ip address is, issue the following command:
```
ifconfig
```[COLOR=Blue]*What follows after "inet addr:" is the ip address for that box.*[/COLOR]

On a fresh install the output of the the nmap command should look something like this:
> Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-08-31 06:39 EDT
Interesting ports on 192.168.0.100:
Not shown: 1992 closed ports
PORT     STATE         SERVICE
[COLOR=Blue]139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds[/COLOR]
631/tcp  open          ipp
68/udp   open|filtered dhcpc
[COLOR=Blue]137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm[/COLOR]
631/udp  open|filtered ipp
5353/udp open|filtered zeroconf
For samba to work the ones marked in blue need to be open.

**3rd: Now find out the ip address of another box on your network and run the nmap command again with it's ip address from the same box you are running right now.** For example, another box on my network is at 192.168.0.101:
```
 sudo nmap -sS -sU -T4 192.168.0.101
```Those same ports need to open on that box as well.

**4th: If all the ports are open proceed to step 5.**
If they are not open post the output of the nmap commands. I don't have any experience with configuring firewalls on linux because I'm behind a router with it's own firewall but it appears redmk2 does.

**5th: Post the output of the following command:**
```
smbtree
```

---

### Post by hawkdog on 2010-08-31
bill@bill-desktop:~$ sudo nmap -sS -sU -T4 192.168.0.108
[sudo] password for bill: 

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-08-31 15:46 EDT
Interesting ports on 192.168.0.108:
Not shown: 1988 closed ports
PORT     STATE         SERVICE
111/tcp  open          rpcbind
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
631/tcp  open          ipp
2049/tcp open          nfs
68/udp   open|filtered dhcpc
111/udp  open|filtered rpcbind
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
631/udp  open|filtered ipp
2049/udp open|filtered nfs
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.41 seconds
bill@bill-desktop:~$ sudo nmap -sS -sU -T4 192.168.0.105

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-08-31 15:47 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 0.37 seconds
bill@bill-desktop:~$ sudo nmap -sS -sU -T4 192.168.0.103

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-08-31 15:48 EDT
Warning: Giving up on port early because retransmission cap hit.


I can ping 192.168.0.103

---

### Post by Morbius1 on 2010-08-31
OK. bill-desktop - 192.168.0.108 looks fine and all the necessary ports seem to be open. Can the Windows box access the Ubuntu shares?

The problem is this one:
> Nmap done: 1 IP address (1 host up) scanned in 1.41 seconds
bill@bill-desktop:~$ sudo nmap -sS -sU -T4 [COLOR=Blue]192.168.0.105[/COLOR]

Starting Nmap 5.00 ( [http://nmap.org]("http://nmap.org/") ) at 2010-08-31 15:47 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 0.37 seconds
Is 192.168.0.105 a Wubi Ubuntu install?
[COLOR=Blue][B]
EDIT:[/B][/COLOR] I forgot - what os is 192.168.0.103 ?

---

### Post by hawkdog on 2010-08-31
bill@bill-desktop:~$  sudo nmap -sS -sU -T4 192.168.0.103
[sudo] password for bill: 

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-08-31 16:14 EDT
Warning: Giving up on port early because retransmission cap hit.
Stats: 0:02:25 elapsed; 0 hosts completed (1 up), 1 undergoing UDP Scan
UDP Scan Timing: About 17.91% done; ETC: 16:27 (0:10:23 remaining)

I redid it and this is what I got.  
192168.0.103 is awubi install
my computers are all running behind a router

---

### Post by Morbius1 on 2010-08-31
Let me see if I got this right:

192.168.0.108 = Ubuntu desktop - bill-desktop - with a "real" ubuntu install

192.168.0.105 = Windows

192.168.0.103 = Wubi install on another box?

If 192.168.0.105 is the Windows box the exact same ports have to be open for Windows to access the shares on bill-desktop and it doesn't appear that they are. Can you temporarily disable the Windows firewall to see if you can access the shares on bill-desktop?

---

### Post by hawkdog on 2010-08-31
i am in the process of making 192.158.0.105 a full ubuntu install

you are correct on the other two

---

### Post by redmk2 on 2010-08-31
> **Morbius1 said:**
> Let me see if I got this right:

192.168.0.108 = Ubuntu desktop - bill-desktop - with a "real" ubuntu install

192.168.0.105 = Windows

192.168.0.103 = Wubi install on another box?

If 192.168.0.105 is the Windows box the exact same ports have to be open for Windows to access the shares on bill-desktop and it doesn't appear that they are. Can you temporarily disable the Windows firewall to see if you can access the shares on bill-desktop?

I still hear that sucking sound.  :D

Some thoughts on the FW issue: It is my opinion that the UFW has been changed in 10.04 (Lucid).  The change is that is that UFW is on by default rather than off as it was in 8.04 (Hardy).

This really causes no one any problems unless the need to use Samba.  Just opening the ports is not all that is needed for Samba.  There is a ***conntrak ***(Connection Tracking in IPTables) setting that allows for stateful packet inspection that needs to be added to the configuration.  See [**_here_**]("http://ubuntuforums.org/showthread.php?p=6924891#post6924891") for Samba and **_[here ]("http://ubuntuforums.org/showthread.php?p=6924891#post6924891")_**for a general description.

So when checking for a FW it is important to see what the config is on the FW, or: **Turn the FW off completely when testing**.  This is the approach @Swerdna takes in his FW section of his [**_Samba guide_**]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall").

---

### Post by hawkdog on 2010-08-31
after converting 192.168.0.105 to ubuntu only  I can see the computer from my desktop ubunt box.  however, when i try to open i get the message  Unable to mount location,  failed to retrieve share list from server

---

### Post by redmk2 on 2010-08-31
> **hawkdog said:**
> after converting 192.168.0.105 to ubuntu only  I can see the computer from my desktop ubunt box.  however, when i try to open i get the message  Unable to mount location,  failed to retrieve share list from server

As a quick test try turning off the firewall.  You can do this by the following command from the terminal command line (CLI):```
sudo UFW disable
```

Then try and browse for the shares.  This might take some time as the "server" (browse master) will need to add the shares to the cache of names.

---

### Post by hawkdog on 2010-08-31
Firewall off on all machines no change

---

### Post by redmk2 on 2010-08-31
> **hawkdog said:**
> Firewall off on all machines no change

From the terminal, what is the output of```
ps -efH | grep mbd
```
[COLOR="purple"]**Edit: ** Also the output of [/COLOR]```
smbtree
```

---

### Post by hawkdog on 2010-08-31
bill@bill-desktop:~$ ps -efH | grep mbd
root       650     1  0 Aug30 ?        00:00:00   smbd -F
root       750   650  0 Aug30 ?        00:00:00     smbd -F
root      2482   650  0 13:53 ?        00:00:00     smbd -F
root      2484   650  0 13:53 ?        00:00:00     smbd -F
root      2972   650  0 15:17 ?        00:00:00     smbd -F
root      2974   650  0 15:17 ?        00:00:00     smbd -F
root      2990   650  0 15:22 ?        00:00:00     smbd -F
root      2992   650  0 15:22 ?        00:00:00     smbd -F
root      3086   650  0 15:29 ?        00:00:00     smbd -F
root      3143   650  0 15:31 ?        00:00:00     smbd -F
root      4118   650  0 18:51 ?        00:00:00     smbd -F
root      4140   650  0 18:51 ?        00:00:00     smbd -F
root      4142   650  0 18:51 ?        00:00:00     smbd -F
root      4194   650  0 19:07 ?        00:00:00     smbd -F
root      4239   650  0 19:09 ?        00:00:00     smbd -F
root      4269   650  0 19:11 ?        00:00:00     smbd -F
root      4271   650  0 19:11 ?        00:00:00     smbd -F
root      4281   650  0 19:12 ?        00:00:00     smbd -F
root      4300   650  0 19:13 ?        00:00:00     smbd -F
root      4302   650  0 19:13 ?        00:00:00     smbd -F
root      4307   650  0 19:13 ?        00:00:00     smbd -F
root      4316   650  0 19:14 ?        00:00:00     smbd -F
root      4642   650  0 19:48 ?        00:00:00     smbd -F
root      4644   650  0 19:48 ?        00:00:00     smbd -F
root      4648   650  0 19:49 ?        00:00:00     smbd -F
root      4669   650  0 19:54 ?        00:00:00     smbd -F
root      1097     1  0 Aug30 ?        00:00:01   nmbd -D
bill      4741  4443  0 20:13 pts/0    00:00:00       grep mbd
bill@bill-desktop:~$ smbtree
Enter bill's password: 
WORKGROUP
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
cli_start_connection: failed to connect to UBUNTU<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
	\\LINUX-LAPTOP   		linux-laptop server (Samba, Ubuntu)
cli_start_connection: failed to connect to LINUX-LAPTOP<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
	\\BILL-DESKTOP   		bill-desktop server (Samba, Ubuntu)
		\\BILL-DESKTOP\documents      	
		\\BILL-DESKTOP\pictures       	
		\\BILL-DESKTOP\software       	
		\\BILL-DESKTOP\IPC$           	IPC Service (bill-desktop server (Samba, Ubuntu))
		\\BILL-DESKTOP\print$         	Printer Drivers

---

### Post by redmk2 on 2010-08-31
> **hawkdog said:**
> bill@bill-desktop:~$ ps -efH | grep mbd
root       650     1  0 Aug30 ?        00:00:00   smbd -F
root       750   650  0 Aug30 ?        00:00:00     smbd -F
...
...
root      4669   650  0 19:54 ?        00:00:00     smbd -F
root      1097     1  0 Aug30 ?        00:00:01   nmbd -D
bill      4741  4443  0 20:13 pts/0    00:00:00       grep mbd
bill@bill-desktop:~$ smbtree
Enter bill's password: 
WORKGROUP
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
cli_start_connection: failed to connect to UBUNTU<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
	\\LINUX-LAPTOP   		linux-laptop server (Samba, Ubuntu)
cli_start_connection: failed to connect to LINUX-LAPTOP<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
	\\BILL-DESKTOP   		bill-desktop server (Samba, Ubuntu)
		\\BILL-DESKTOP\documents      	
		\\BILL-DESKTOP\pictures       	
		\\BILL-DESKTOP\software       	
		\\BILL-DESKTOP\IPC$           	IPC Service (bill-desktop server (Samba, Ubuntu))
		\\BILL-DESKTOP\print$         	Printer Drivers

Lets see what you get with```
nmblookup -d2 -w UBUNTU
```

---

### Post by hawkdog on 2010-08-31
bill@bill-desktop:~$ nmblookup -d2 -w UBUNTU
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
added interface eth0 ip=fe80::240:caff:fe33:10c8%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.108 bcast=192.168.0.255 netmask=255.255.255.0
querying UBUNTU on 192.168.0.255
Got a positive name query response from 192.168.0.103 ( 192.168.0.103 )
192.168.0.103 UBUNTU<00>
bill@bill-desktop:~$ nmblookup -d2 -w LINUX-LAPTOP
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
added interface eth0 ip=fe80::240:caff:fe33:10c8%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.108 bcast=192.168.0.255 netmask=255.255.255.0
querying LINUX-LAPTOP on 192.168.0.255
Got a positive name query response from 192.168.0.105 ( 192.168.0.105 )
192.168.0.105 LINUX-LAPTOP<00>
bill@bill-desktop:~$

---

### Post by redmk2 on 2010-08-31
> **hawkdog said:**
> ```
bill@bill-desktop:~$ nmblookup -d2 -w UBUNTU
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
added interface eth0 ip=fe80::240:caff:fe33:10c8%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.108 bcast=192.168.0.255 netmask=255.255.255.0
querying UBUNTU on 192.168.0.255
Got a positive name query response from 192.168.0.103 ( 192.168.0.103 )
192.168.0.103 UBUNTU<00>
```

```
bill@bill-desktop:~$ nmblookup -d2 -w LINUX-LAPTOP
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
added interface eth0 ip=fe80::240:caff:fe33:10c8%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.108 bcast=192.168.0.255 netmask=255.255.255.0
querying LINUX-LAPTOP on 192.168.0.255
Got a positive name query response from 192.168.0.105 ( 192.168.0.105 )
192.168.0.105 LINUX-LAPTOP<00>
bill@bill-desktop:~$
```

It is much easier to read this stuff if you surround the data with ```
 [/code ] or use the advanced setting for the editor and selecting the ***[SIZE="3"]# [/SIZE]***icon at the top right.

It appears that the the host Ubuntu is working as far as NetBIOS is concerned.  Thats good.

Let's use some Morbius1 tests.  What is the output (again) of:[CODE]
net usershare info

testparm -s
```
[COLOR="Purple"]**Edit: **How about we also have */etc/hosts* files for both hosts in question.[/COLOR]

---

### Post by hawkdog on 2010-08-31
Sorry but I con't know how to do what your asking


bill@bill-desktop:~$ net usershare info
[documents]
path=/home/bill/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

[pictures]
path=/home/bill/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[software]
path=/home/bill/Desktop/Software
comment=
usershare_acl=Everyone:R,
guest_ok=y

info_fn: file /var/lib/samba/usershares/presario is not a well formed usershare file.
info_fn: Error was Path is not a directory.


bill@bill-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

---

### Post by redmk2 on 2010-08-31
> Sorry but I con't know how to do what your asking


The output of ```
cat /etc/hosts
```

As far as formating: put everything inside of this:

[code]

minus the space between these: / code 

[/ code]

**Edit:** Or if you want he **#** icon you can use quick reply and check advanced.  Then follow my instructions above.

---

### Post by redmk2 on 2010-08-31
> **hawkdog said:**
> Sorry but I con't know how to do what your asking


```
bill@bill-desktop:~$ net usershare info
[documents]
path=/home/bill/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

[pictures]
path=/home/bill/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[software]
path=/home/bill/Desktop/Software
comment=
usershare_acl=Everyone:R,
guest_ok=y

[COLOR="Red"][B]info_fn: file /var/lib/samba/usershares/presario is not a well formed usershare file.
info_fn: Error was Path is not a directory.[/B][/COLOR]


bill@bill-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
```

The items in red are disturbing.  You should delete them.

---

### Post by hawkdog on 2010-08-31
```

bill@bill-desktop:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	bill-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
bill@bill-desktop:~$ 


```


The item in red was used as path to a windows installation on another hard drive in this computer

---

### Post by redmk2 on 2010-08-31
> **hawkdog said:**
> ```

bill@bill-desktop:~$ cat /etc/hosts
127.0.0.1	localhost
**[COLOR="green"]127.0.1.1[/COLOR]**	bill-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
bill@bill-desktop:~$ 

```
The item in red was used as path to a windows installation on another hard drive in this computer

Delete that share.  It is causing an error.  You can always add it back later.  Don't quote me on this, but I believe you can only create a share it after you mount the partition in the local file system. 

The item in **[COLOR="Green"]green [/COLOR]**needs to be the IP address of the Ethernet or wireless NIC (interface).  This is a mapping between the  hostname **bill-desktop** and  valid LAN network address.  In fact the only address localhost should have is 127.0.0.1 or something in the 127.0.0.0/8 subnet.  This address (127.0.0.1) is a virtual address.  It allows the host to talk to itself ONLY.

Here is my /etc/hosts file
```
red@**granite**:~>cat /etc/hosts
127.0.0.1       localhost
[COLOR="green"]**192.168.1.2**[/COLOR]     **granite**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I have another machine named **onyx** (192.168.1.3).  If I ping **onyx **from **granite **what I really am doing is pinging 192.168.1.3 from 192.168.2.  The host name is translated into the  numerical.

I would check ALL of your installs to insure that they are all correct.  Why dont you list the IP addresses and hostnames like this:
<IP Address>  <hostname>

Then we will be able to make sure the /etc/hosts files are correct.

---

### Post by Morbius1 on 2010-09-01
redmk2, So far I haven't disagreed with anything you've written in this thread. And I'll admit that what little knowledge I have on this is more on the Samba end than the network end, but ....
[B]
[1] Usershare error[/B]
> [QUOTE][COLOR=Red]info_fn: file /var/lib/samba/usershares/presario is not a well formed usershare file.
info_fn: Error was Path is not a directory.[/COLOR]The items in red are disturbing.  You should delete them.[/QUOTE]He can't delete them - at least not graphically. It's a Nautilus-share ( since we're being super accurate in this thread the correct term is usershare ) and it will be ignored by samba. If you really want to delete the share definition you could just go to /var/lib/samba/usershare and simply delete the "presario" file or you can use a command:
```
net usershare delete presario
```But again it really doesn't matter if it's not deleted.

**[2] /etc/hosts**
This is the applicable section of my own hosts file:
> 
127.0.0.1    localhost
[COLOR=Blue]127.0.1.1    morbius[/COLOR]
I think that's the way it should be: Debian Reference Manual: [http://qref.sourceforge.net/quick/ch-gateway.en.html](http://qref.sourceforge.net/quick/ch-gateway.en.html)
> **10.4 Domain Name Service (DNS)**

   Hosts are referred to by domain name as well as by IP address.  DNS is a client-server system in which name resolvers consult nameservers in order to associate domain names with IP addresses and other properties of hosts.  The GNU C Library resolver(3) can also look up IP addresses in files or consult Network Information Services (NIS). 
   Some software (e.g., GNOME) expects the system hostname to be resolvable to an IP address with a canonical fully qualified domain name.  This is really improper because system hostnames and domain names are two very different things; but there you have it.  In order to support that software, it is necessary to ensure that the system hostname can be resolved.  Most often this is done by putting a line in /etc/hosts containing some IP address and the system hostname. [COLOR=Blue] If your system has a permanent IP address then use that; otherwise use the address 127.0.1.1. [/COLOR]
          127.0.0.1 localhost
        127.0.1.1 uranus
  To see whether your system hostname can be resolved to an IP address with a fully qualified domain name, use the hostname --fqdn command. 
When I do a "hostname --fqdn" it does return "morbius" Your suggestion that he use a specific ip address will work obviously but hawkdog ( or any average user ) may not have static ip addresses on his systems.

**[3] **The other machines.
It appears we have three machines on this network:
192.168.0.103  UBUNTU
192.168.0.105  LINUX-LAPTOP
192.168.0.108  BILL-DESKTOP
[COLOR=Blue]*At least these are the ip address at the moment. A reboot of these machines my change that.*[/COLOR]

Everything about "BILL-DESKTOP" now appears to be in order and the output of smbtree confirms that by displaying , without errors, that machine and all it's shares. If you all remember the first time hawkdog ran smbtree from BILL-DESKTOP his own machine did not show up. Restoring the default smb.conf fixed that. 

I think we need to move our queries from BILL-DESKTOP to one of the other machines. nmblookup did find the other boxes and their ip addresses so perhaps it's another bad samba configuration or a firewall or maybe even apparmor. What is the output of the following commands from the "UBUNTU" machine:
```
net usershare info
``````
testparm -s
``````
smbtree
```

---

### Post by redmk2 on 2010-09-01
> **Morbius1]He can't delete them - at least not graphically.[/QUOTE]
I was just trying to get all the errors eliminated.  I haven't created usershares at all.  If they are not a bother then let them stay.


[QUOTE=hawkdog]I am going to try the static approach also reconfigure everything.[/QUOTE]

I think the hosts file issue is more important.  I thought the OP was using static IP's.  At least he said he was going to do.  The passage you quoted is true.  The part you highlighted is really a last resort to cure a bug in GNOME a long time ago.  More directly to the point is the section just before it:

[QUOTE]Some software (e.g., GNOME) expects the system hostname to be resolvable to an IP address with a canonical fully qualified domain name. This is really improper because system hostnames and domain names are two very different things said:**
> This is the Gnome Bug.

[QUOTE] In order to support that software, it is necessary to ensure that the system hostname can be resolved. *Most often this is done by putting a line in /etc/hosts containing **some **IP address and the system hostname.*

I agree that if you have DHCP assigning IP addresses this needs to be **SOME **static IP address and 127.0.1.1 will work for the Gnome bug.  My guess is that this was long ago and is not needed any more.

[COLOR="Purple"]**Edit:** If the OP can post the output of [/COLOR]```
cat /etc/network/interfaces
```[COLOR="Purple"]We can see if he is using static or DHCP supplied addressing.[/COLOR]

---

### Post by Morbius1 on 2010-09-01
> I agree that if you have DHCP assigning IP addresses this needs to be **SOME **static IP address and 127.0.1.1 will work for the Gnome bug.  My guess is that this was long ago and is not needed any more.Although I've never given any thought as to how it does this, Samba by default will use the name in the hosts file, if I recall correctly, to broadcast it's name to the network. Even if the only thing in hosts was localhost you can give it one in smb.conf itself with a "netbios name =" entry.

---

### Post by hawkdog on 2010-09-01
```
bill@ubuntu:~$ net usershare info
[mshome]
path=/home/bill/Desktop/MSHOME
comment=
usershare_acl=Everyone:F,
guest_ok=y

[downloads]
path=/home/bill/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/system volume information is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[pictures]
path=/home/bill/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[documents]
path=/home/bill/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

```
bill@ubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```


```
bill@ubuntu:~$ smbtree
Enter bill's password: 
WORKGROUP
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
		\\UBUNTU\mshome         	
		\\UBUNTU\downloads      	
		\\UBUNTU\pictures       	
		\\UBUNTU\documents      	
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
		\\UBUNTU\print$         	Printer Drivers
	\\LINUX-LAPTOP   		linux-laptop server (Samba, Ubuntu)
cli_start_connection: failed to connect to LINUX-LAPTOP<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
	\\BILL-DESKTOP   		bill-desktop server (Samba, Ubuntu)
cli_start_connection: failed to connect to BILL-DESKTOP<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
	\\BARBARA-PC     		
cli_start_connection: failed to connect to BARBARA-PC<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED

```

I am NOT using static ip addresses

---

### Post by Morbius1 on 2010-09-01
Would you provide the make and model of your router please.

---

### Post by hawkdog on 2010-09-01
Morbius1

i really appreciate your hanging in there with me.  As I stated before, I am new to linux.  I am pretty familiar with windows but I have been looking for a replacement.  Everything was working as I needed until I added multiple linux compurters.  I don't consider myself computer challanged but my mind is beginning to be blown over the difference in nomenclature and the way things interact,

Anyway, (and I hope this dosen't blow your mind) but I have two routers.  This allows me wifi access from different levels of my house.

D-Link DI624  at 192.168.0.1
Linksys WRT54G at 192.168.0.2

The desktop connects to the dlink the rest to the linksys.
Also, it seems that the dhcp service is disabled in both.

Hope I have not confused you any further.

---

### Post by Morbius1 on 2010-09-01
> i really appreciate your hanging in there with me.So far I haven't been any help to you whatsoever but thanks just the same. I admire anyone who has stayed with this as long as you have especially the way you were ignored there for a while. 

> Anyway, (and I hope this dosen't blow your mind) but I have two routers.   This allows me wifi access from different levels of my house.

D-Link DI624  at 192.168.0.1
Linksys WRT54G at 192.168.0.2

The desktop connects to the dlink the rest to the linksys.
Also, it seems that the dhcp service is disabled in both.Too late - mind blown. :cry:

Please tell me that one is configured as a Wireless Access Point to the other. Or are they two independent routers with their own separate clients.

---

### Post by hawkdog on 2010-09-01
They are connected by cable.

---

### Post by redmk2 on 2010-09-01
> **hawkdog][COLOR="Red"]**I am NOT using static ip addresses**[/COLOR][/QUOTE]
Your not?  What are you using then?

[QUOTE=hawkdog said:**
> ...

Anyway, (and I hope this dosen't blow your mind) but I have two routers.  This allows me wifi access from different levels of my house.

D-Link DI624  at 192.168.0.1
Linksys WRT54G at 192.168.0.2

The desktop connects to the dlink the rest to the linksys.
[COLOR="Red"]**Also, it seems that the dhcp service is disabled in both.**[/COLOR]
So if it is not static and it is not DHCP, then what the heck is it?> 

Hope I have not confused you any further.

You have confused me.

---

### Post by hawkdog on 2010-09-01
Sorry looks like the linksys router is the dhcp server.

---

### Post by redmk2 on 2010-09-01
> **Morbius1 said:**
> Although I've never given any thought as to how it does this, Samba by default will use the name in the hosts file, if I recall correctly, to broadcast it's name to the network. Even if the only thing in hosts was localhost you can give it one in smb.conf itself with a "netbios name =" entry.

So from the Samba.org site on [**_Performance and Reliability _**]("http://www.samba.org/samba/docs/man/Samba-Guide/HA.html#id2619530"): [COLOR="Navy"]"When configured as a DHCP client, a number of Linux distributions set the system hostname to localhost. If the parameter netbios name is not specified to something other than localhost, the Samba server appears in the Windows Explorer as LOCALHOST. Moreover, the entry in the /etc/hosts on the Linux server points to IP address 127.0.0.1. This means that when the Windows client obtains the IP address of the Samba server called LOCALHOST, it obtains the IP address 127.0.0.1 and then proceeds to attempt to set up a NetBIOS over TCP/IP connection to it. This cannot work, because that IP address is the local Windows machine itself. Hostnames must be valid for Windows networking to function correctly."[/COLOR]

I think rather than beating on this dead horse I will just butt out. :-) 

The OP has an unusual setup that gets more interesting every day.  As you say you are "sucked in".

---

### Post by redmk2 on 2010-09-01
> **hawkdog said:**
> Sorry looks like the linksys router is the dhcp server.

Sorry,  I can't resist.  Is one of these routers being used as an AP only?

---

### Post by hawkdog on 2010-09-01
> **redmk2 said:**
> Sorry,  I can't resist.  Is one of these routers being used as an AP only?
By ap i am assuming you mean access point.  One compurter is using the dlink as an access and the others are using the linksys.

---

### Post by redmk2 on 2010-09-01
> **hawkdog said:**
> By ap i am assuming you mean access point.  One compurter is using the dlink as an access and the others are using the linksys.

Good.  That makes sense.

Let's try one thing again.  Run *smbtree *again but **with more diagnostics**.  post the output of```
smbtree -d4
```

If it helps you can send it to a text file first.  Like this```
smbtree -d4 > tree.txt
```

---

### Post by capscrew on 2010-09-01
> **redmk2 said:**
> So from the Samba.org site on [**_Performance and Reliability _**]("http://www.samba.org/samba/docs/man/Samba-Guide/HA.html#id2619530"): [COLOR="Navy"]"When configured as a DHCP client, a number of Linux distributions set the system hostname to localhost. If the parameter netbios name is not specified to something other than localhost, the Samba server appears in the Windows Explorer as LOCALHOST. Moreover, the entry in the /etc/hosts on the Linux server points to IP address 127.0.0.1. This means that when the Windows client obtains the IP address of the Samba server called LOCALHOST, it obtains the IP address 127.0.0.1 and then proceeds to attempt to set up a NetBIOS over TCP/IP connection to it. This cannot work, because that IP address is the local Windows machine itself. Hostnames must be valid for Windows networking to function correctly."[/COLOR]

I think rather than beating on this dead horse I will just butt out. :-) 

The OP has an unusual setup that gets more interesting every day.  As you say you are "sucked in".

+1

Capscrew

---

### Post by Morbius1 on 2010-09-01
> [COLOR=Black]This means that when the Windows client obtains the  IP address of the Samba server called LOCALHOST, it obtains the IP  address 127.0.0.1 and then proceeds to attempt to set up a NetBIOS over  TCP/IP connection to it. This cannot work, because that IP address is  the local Windows machine itself. Hostnames must be valid for Windows  networking to function correctly."[/COLOR]
Unless you read all the way to my last sentence:
> Even if the only thing in hosts was localhost you can give it one in smb.conf itself with a [COLOR=Blue]"netbios name ="[/COLOR] entry.     

---

### Post by hawkdog on 2010-09-01
You did not specify which computer.  The file I am posting is from the Ubuntu computer.

/home/bill/tree.txt

---

### Post by capscrew on 2010-09-01
> **Morbius1 said:**
> Unless you read all the way to my last sentence:

But of course.  I was only acknowledging @redmk2's assessment of the roll that the **/etc/hosts** file plays.

---

### Post by redmk2 on 2010-09-01
> **hawkdog said:**
> You did not specify which computer.  The file I am posting is from the Ubuntu computer.

/home/bill/tree.txt

I don't think it really matters right now.  The tree will be built from all Samba shares.

On the other hand, are you telling me that the results are different from different hosts?

**Edit: **post what you have and we will go from there.

---

### Post by Morbius1 on 2010-09-01
> **hawkdog said:**
> You did not specify which computer.  The file I am posting is from the Ubuntu computer.

/home/bill/tree.txt
You didn't post the file correctly. All we can see is the path name.

---

### Post by hawkdog on 2010-09-01
reply

---

### Post by redmk2 on 2010-09-01
> **hawkdog said:**
> reply

I see some trouble```
[B][COLOR="Red"]resolve_hosts: Attempting host lookup for name UBUNTU<0x20>
Connecting to 127.0.1.1 at port 445
[/COLOR][/B]
```

This only works for the host you are on.  you need to edit the smb.conf file on this host and add a nebios name.

```
[COLOR="red"][B]resolve_hosts: Attempting host lookup for name LINUX-LAPTOP<0x20>
Connecting to 63.251.179.13 at port 445
Connecting to 63.251.179.13 at port 139
Error connecting to 63.251.179.13 (Connection refused)
Connecting to 8.15.7.117 at port 445
[/B][/COLOR]
```

These appear to be Internet IP addresses for DNS servers.  This looks to be a problem involving your DNS setup.  Maybe the ISP's doing?

And more```
[COLOR="Red"][B]resolve_hosts: Attempting host lookup for name BARBARA-PC<0x20>
Connecting to 8.15.7.117 at port 445
Connecting to 8.15.7.117 at port 139
Error connecting to 8.15.7.117 (Connection refused)
Connecting to 63.251.179.13 at port 445
Connecting to 63.251.179.13 at port 139
Error connecting to 63.251.179.13 (Connection refused)
cli_start_connection: failed to connect to BARBARA-PC<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
[/B][/COLOR]
```
[COLOR="Purple"]**Edit: **I would like to see this same test run on ALL of the Linux hosts.

Just a guess but I believe that you will ultimately need to add NetBIOS names to all of these for this setup to work.[/COLOR]

---

### Post by hawkdog on 2010-09-01
Ok.  Like I have said before, you guys have been a great help and I appreciate you hanging in there.  I understand your desire to find exactly what is wrong with my installation.  I have been there,  It is a great challenge.  It is what we have been trained for; to find out what is wrong. However, at some point the best solution is to start over from scratch.  

With the exception of the desktop, all of my computers are virgin installations.  The desktop (as far as the smbconf) is back to normal.  Right now I can see all computers from the windows box,  I can't see anything from the linux boxes.

I am willing to travel down whatever path you all want.  If you want to continue as we have been fine.  If you are frustrated and want to drop out, I understand.  If you want to start from scratch, fine just tell me how to do it.

Thanks

Bill

---

### Post by redmk2 on 2010-09-01
> **hawkdog said:**
> Ok.  Like I have said before, you guys have been a great help and I appreciate you hanging in there.  I understand your desire to find exactly what is wrong with my installation.  I have been there,  It is a great challenge.  It is what we have been trained for; to find out what is wrong. However, at some point the best solution is to start over from scratch.  

With the exception of the desktop, all of my computers are virgin installations.  The desktop (as far as the smbconf) is back to normal.  Right now I can see all computers from the windows box,  I can't see anything from the linux boxes.

I am willing to travel down whatever path you all want.  If you want to continue as we have been fine.  If you are frustrated and want to drop out, I understand.  If you want to start from scratch, fine just tell me how to do it.

Thanks

Bill

Look at post #100.  The [COLOR="Red"]**stuff in red**[/COLOR] explains your problem.

At this point I believe all you need to do is edit the smb.conf file on each Linux host and add a NetBIOS name. Make a copy first (i.e. smb.conf.original)

To edit the smb.conf file from the CLI you would use this```
sudo nano /etc/samba/smb.conf
```

You need to add this to the [global] section on each machine.  Substitute the the appropriate hostname for each machine.
```
netbios name = <TheHostName>
```

When done you can follow the instructions at the bottom of the screen to save and close the editor.  Then you can restart the Samba services with ```
sudo service smbd restart
sudo service nmbd restart
```

Ask if you have further questions.

---

### Post by Morbius1 on 2010-09-02
redmk2 and capscrew ( if you're out there ), I'm not questioning your expertise in any way. This is truly just a question.

Samba goes through a preset order to resolve names. If I run smbtree -d4 on my own network I get this ( abbreviated ) response when accessing another machine:
> Connecting to host=MORBIUS2
resolve_lmhosts: Failed ( there is no /etc/samba/lmhosts )
resolve_wins: Failed ( I have no WINS server )
resolve_hosts: Failed ( the only entry in hosts is Morbius1 )
name_resolve_bcast: Attempting broadcast lookup for name MORBIUS2<0x20>
nmb packet from 192.168.0.110(137) header: id=6858 opcode=Query(0) response=Yes[COLOR=Blue]*That is the correct ip address for MORBIUS2*[/COLOR]

On hawkdog's network he gets this ( again abbreviated ):
> Connecting to host=BILL-DESKTOP
resolve_lmhosts: Failed ( there is no /etc/samba/lmhosts )
resolve_wins: Failed ( There is no WINS server )
resolve_hosts: Attempting host lookup for name BILL-DESKTOP<0x20>
Connecting to 63.251.179.13 at port 445
Connecting to 63.251.179.13 at port 139
Error connecting to 63.251.179.13 (Connection refused)
Connecting to 8.15.7.117 at port 445
Connecting to 8.15.7.117 at port 139
Error connecting to 8.15.7.117 (Connection refused)
cli_start_connection: failed to connect to BILL-DESKTOP<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
Couple of things:
Why does it appear it's trying to reach his ISP's DNS servers?
Why doesn't it ever get to bcast?

If I rearrange the order of name resolution in smb.conf ( name resolve order = bcast lmhosts host wins ) it finds MORBIUS2 immediately and skips the other methods:
> Connecting to host=MORBIUS2
name_resolve_bcast: Attempting broadcast lookup for name MORBIUS2<0x20>
Got a positive name query response from 192.168.0.110 ( 192.168.0.110 )
Connecting to 192.168.0.110 at port 445Hawkdog's system is trying 3 different methods and getting stuck on one without getting to the only method that works by default in linux. 

Will rearranging the order putting bcast first solve his problem?

NOTE: I'm still not sure how these two routers are connected to each other - is one a WAP or not? I don't know if bcast works across different subnets.

---

### Post by redmk2 on 2010-09-02
> **Morbius1 said:**
> redmk2 and capscrew ( if you're out there ), I'm not questioning your expertise in any way. This is truly just a question.
[COLOR="Navy"]**Edit:**I'm adding this at the top so it won't be missed.  For a more detailed look at what is going on add more logging.  Try this:[/COLOR]```
smbtree -d6 > someFileName
```> 

Samba goes through a preset order to resolve names. If I run smbtree -d4 on my own network I get this ( abbreviated ) response when accessing another machine:```
Connecting to host=MORBIUS2
resolve_lmhosts: Failed ( there is no /etc/samba/lmhosts )
resolve_wins: Failed ( I have no WINS server )
resolve_hosts: Failed ( the only entry in hosts is Morbius1 )
name_resolve_bcast: Attempting broadcast lookup for name MORBIUS2<0x20>
nmb packet from 192.168.0.110(137) header: id=6858 opcode=Query(0) response=Yes
```
[COLOR=Blue]*That is the correct ip address for MORBIUS2*[/COLOR]

On hawkdog's network he gets this ( again abbreviated ):
Couple of things:```
Connecting to host=BILL-DESKTOP
resolve_lmhosts: Failed ( there is no /etc/samba/lmhosts )
resolve_wins: Failed ( There is no WINS server )
resolve_hosts: [COLOR="Red"]Attempting host lookup[/COLOR] for name BILL-DESKTOP<0x20>
Connecting to 63.251.179.13 at port 445
Connecting to 63.251.179.13 at port 139
Error connecting to 63.251.179.13 (Connection refused)
Connecting to 8.15.7.117 at port 445
Connecting to 8.15.7.117 at port 139
Error connecting to 8.15.7.117 (Connection refused)
cli_start_connection: failed to connect to BILL-DESKTOP<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
```
Why does it appear it's trying to reach his ISP's DNS servers?
Why doesn't it ever get to bcast?
I'll bet the OP has configured the /etc/resolv file to point to his ISP's DNS. It appears that the DNS never stops trying. The DNS upstream should never receive LAN side name requests in the first place, but it does and we have to deal with it.  

Since the OP has confirmed that he  is using DHCP  we need to provide the NetBIOS name in another manner.  As you pointed out: since we can't use the /etc/hosts to reliably set the DNS name of the host, we need to use the *[COLOR="Navy"]netbios name = <someName>[/COLOR]* in smb.conf.> 

If I rearrange the order of name resolution in smb.conf ( name resolve order = bcast lmhosts host wins ) it finds MORBIUS2 immediately and skips the other methods: ...

Hawkdog's system is trying 3 different methods and getting stuck on one without getting to the only method that works by default in linux. 

Will rearranging the order putting bcast first solve his problem?
I'm not big on altering the smb.conf file in idiosyncratic ways.  The order of name checking does matter.  What would work here may not work for others reading this later on.

For sure it would make it b'cast first.  But I think it would fail without a NetBIOS name in the smb.conf file  I think a more appropriate method would be to
[LIST=1]
[*]Edit the /etc/resolv file to point to the LAN router for DNS resolution first.
[*]Edit the smb.conf file to add the netBios name there
[/LIST]
> 
NOTE: I'm still not sure how these two routers are connected to each other - is one a WAP or not? 
One is a WAP and it should be on the same subnet.> 

I don't know if bcast works across different subnets.
Under normal conditions b'casts don't cross subnet boundaries.

---

### Post by bowsprit on 2010-09-11
I've been lurking on this thread b/c I have a similar problem -- my windows computers couldn't see (or resolve the name of) my linux 10.04 box. 

The advice to disable ufw solved all my problems. 

Now, I'm a networking newbie and hope to stay that way. I've been running this box with pretty much the same settings on a simple home network since ubuntu 6, and upgrading automatically each time. I've never messed with ufw. Somehow it decided to block my samba setup and made me very frustrated :) 

So, question: 
The only steps I've taken now were "sudo ufw disable" -- good for now -- but what should I do to make ufw and samba play nice together?

---

### Post by bodhi.zazen on 2010-09-11
> **bowsprit said:**
> I've been lurking on this thread b/c I have a similar problem -- my windows computers couldn't see (or resolve the name of) my linux 10.04 box. 

The advice to disable ufw solved all my problems. 

Now, I'm a networking newbie and hope to stay that way. I've been running this box with pretty much the same settings on a simple home network since ubuntu 6, and upgrading automatically each time. I've never messed with ufw. Somehow it decided to block my samba setup and made me very frustrated :) 

So, question: 
The only steps I've taken now were "sudo ufw disable" -- good for now -- but what should I do to make ufw and samba play nice together?

You have to allow the samba ports.

The ports you need to allow are listed here:

[http://troy.jdmz.net/samba/fw/](http://troy.jdmz.net/samba/fw/)

Do you know how to configure ufw to allow those ports ?

---

