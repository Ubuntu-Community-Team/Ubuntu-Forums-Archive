---
title: "Galaxy S Phone DLNA fix"
date: 2010-08-12
forum: Mythbuntu
---

### Post by yzfr1 on 2010-08-12
Anyone know how to apply this patch?

Sorry, I am an noob.  

I just got a Samsung Captivate and I can't stream to my phone via DLNA. I found this and I think it is same problem as on this link.  

I updated my system with apt-get upgrade and it still doesn't work.

So I figure I need to apply this patch but I don't want to mess my system up as this person does not say they are using Mythbuntu.

Here is the link of what I think I need to do.

[http://svn.mythtv.org/trac/ticket/8678](http://svn.mythtv.org/trac/ticket/8678)

Thanks in advance.

---

### Post by yzfr1 on 2010-08-13
Ok.. maybe I title this a little wrong..  but this is a MythTV issue.  Does no one know how this works?

---

### Post by ian dobson on 2010-08-13
Hi,

As written in your link
apt-get source mythtv
apt-get build-dep mythtv
cd mythtv-0.23.0+fixes24158/
patch -p1 <patch.txt 
dpkg-buildpackage
cd ..
dpkg -i libmyth-0.23-0_0.23.0+fixes24158-0ubuntu2_amd64.deb libmyth-python_0.23.0+fixes24158-0ubuntu2_all.deb \
    mythtv-backend_0.23.0+fixes24158-0ubuntu2_amd64.deb mythtv-backend-master_0.23.0+fixes24158-0ubuntu2_all.deb \
    mythtv-common_0.23.0+fixes24158-0ubuntu2_amd64.deb mythtv-database_0.23.0+fixes24158-0ubuntu2_all.deb \
    mythtv-frontend_0.23.0+fixes24158-0ubuntu2_amd64.deb \
    mythtv-transcode-utils_0.23.0+fixes24158-0ubuntu2_amd64.deb
restart mythtv-backend

where patch.txt contains the patch you want so apply.

Not something for a newbie. Maybe wait until the patch is applied to the fixes branch and use the autobuild version of mythbuntu.

Regards
Ian Dobson

---

### Post by yzfr1 on 2010-08-13
> **ian dobson said:**
> Hi,

As written in your link
apt-get source mythtv
apt-get build-dep mythtv
cd mythtv-0.23.0+fixes24158/
patch -p1 <patch.txt 
dpkg-buildpackage
cd ..
dpkg -i libmyth-0.23-0_0.23.0+fixes24158-0ubuntu2_amd64.deb libmyth-python_0.23.0+fixes24158-0ubuntu2_all.deb \
    mythtv-backend_0.23.0+fixes24158-0ubuntu2_amd64.deb mythtv-backend-master_0.23.0+fixes24158-0ubuntu2_all.deb \
    mythtv-common_0.23.0+fixes24158-0ubuntu2_amd64.deb mythtv-database_0.23.0+fixes24158-0ubuntu2_all.deb \
    mythtv-frontend_0.23.0+fixes24158-0ubuntu2_amd64.deb \
    mythtv-transcode-utils_0.23.0+fixes24158-0ubuntu2_amd64.deb
restart mythtv-backend

where patch.txt contains the patch you want so apply.

Not something for a newbie. Maybe wait until the patch is applied to the fixes branch and use the autobuild version of mythbuntu.

Regards
Ian Dobson

Thanks Ian....

I guess I was just checking to make sure this won't mess up my Mythbuntu install.

I can do this part of building of the package.  I seem to mess with my system sometimes and I spend days getting things to work again.

Is rebuilding the mythtv package going to make me spend days or weeks fixing things?

---

### Post by ian dobson on 2010-08-14
Hi,

As I've said it's not something a newbie should try, it could well break your mythtv installation.

Have you enabled autobuilds? The patch appears to be for the fixes branch (which is the autobuild package in Mythbuntu).

So maybe just enable the autobuilds and see if the patch has made it into the branch.

Regards
Ian Dobson

---

