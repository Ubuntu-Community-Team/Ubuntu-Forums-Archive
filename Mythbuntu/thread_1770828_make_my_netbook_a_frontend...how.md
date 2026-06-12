---
title: "make my netbook a frontend...how?"
date: 2011-05-29
forum: Mythbuntu
---

### Post by geekyhawkes on 2011-05-29
Hey guys, i would like to make my netbook a myth frontend, its already running ubunutu 9.04 and has an 8gb ssd.  Is it as simple as sudo apt-get install mythtv?

What sort of free space do i need for mythtv? Is there a different install for frontend only? 

Thanks

---

### Post by klc5555 on 2011-05-29
First of all, the frontend and whatever your backend is have to be running the same version of mythtv. Otherwise they can't connect because of protocol mismatch. A 9.04 netbook will run mythtv 0.21 (protocol 40) by default. Depending on your backend version, you may need to upgrade the netbook. .deb packages for later versions of mythtv will likely not install nor run on 9.04 because of dependency issues.

If you have the same mythtv version and OS versions that will work together, you need two .deb packages to set up a remote frontend-only: mythtv-common and mythtv-frontend. Space requirements just a few Megs.

On the backend, mysql has to be set up in mythbuntu control center to accept remote connections. In the backend setup, all references to localhost or 127.0.0.1 have to be changed to the machine's real IP address. The PIN number should be set to 0000

On the netbook, run "mythfrontend" from a prompt. It will kick you to a config screen where the backend's IP address, the database name ("mythconverg"), the username ("mythtv") and the mysql password (located on the backend in /home/mythtv/.mythtv/mysql.txt among other places) can all be entered. When this is all entered, if everything is set up properly, the frontend should churn around for a few moments and start loading the G.A.N.T. theme and you're in business. If it gives a "can't login to database" error, then something is configured wrong and mythfrontend will kick you back to its configuration screen.

---

### Post by tgm4883 on 2011-05-29
> **klc5555 said:**
> First of all, the frontend and whatever your backend is have to be running the same version of mythtv. Otherwise they can't connect because of protocol mismatch. A 9.04 netbook will run mythtv 0.21 (protocol 40) by default. Depending on your backend version, you may need to upgrade the netbook. .deb packages for later versions of mythtv will likely not install nor run on 9.04 because of dependency issues.

If you have the same mythtv version and OS versions that will work together, you need two .deb packages to set up a remote frontend-only: mythtv-common and mythtv-frontend. Space requirements just a few Megs.

On the backend, mysql has to be set up in mythbuntu control center to accept remote connections. In the backend setup, all references to localhost or 127.0.0.1 have to be changed to the machine's real IP address. The PIN number should be set to 0000

On the netbook, run "mythfrontend" from a prompt. It will kick you to a config screen where the backend's IP address, the database name ("mythconverg"), the username ("mythtv") and the mysql password (located on the backend in /home/mythtv/.mythtv/mysql.txt among other places) can all be entered. When this is all entered, if everything is set up properly, the frontend should churn around for a few moments and start loading the G.A.N.T. theme and you're in business. If it gives a "can't login to database" error, then something is configured wrong and mythfrontend will kick you back to its configuration screen.

Ubuntu 9.04 has builds for 0.22 - 0.23.1, not 0.21 (are you thinking of 8.04?). There is a complete build list that the Mythbuntu team provides at

[http://mythbuntu.org/files/mythbuntu-repos.db](http://mythbuntu.org/files/mythbuntu-repos.db)

The rest is correct. I'd also add that your netbook will probably only handle SD content, unless you can do vdpau on it.

---

### Post by klc5555 on 2011-05-30
Nope. Actually I was thinking about 9.04 /0.21, which I'm running this very moment on 3 machines. 0.21 20080304-1 19961 to be precise. I also have a couple of laptops running straight Xubuntu 10.04 which I'm using as remote frontends by using the old mythtv-0.21 .debs from 9.04. The old .debs still run on 10.04, once the dependencies are fixed.

The linked repos.db seems only to list builds back to Karmic. I imagine 9.04 (Jaunty) is simply too old to be listed. 

9.04 was the last version that shipped with myth 0.21, which made my upgrade to it directly from 7.10 + 0.21 backports (skipping 8.04 and 8.10) very simple at the time, using the old-fashioned backup database/wipe/clean install/restore database method. I don't know if 0.22 builds were ever composed for 9.04. If there were in fact 0.22 or 0.23 builds made available for 9.04, it may make the OP's task easier, if he can find them. Canonical only archives distribution-level Mythbuntu, so far as I know.

---

### Post by tgm4883 on 2011-05-30
> **klc5555 said:**
> Nope. Actually I was thinking about 9.04 /0.21, which I'm running this very moment on 3 machines. 0.21 20080304-1 19961 to be precise. I also have a couple of laptops running straight Xubuntu 10.04 which I'm using as remote frontends by using the old mythtv-0.21 .debs from 9.04. The old .debs still run on 10.04, once the dependencies are fixed.

The linked repos.db seems only to list builds back to Karmic. I imagine 9.04 (Jaunty) is simply too old to be listed. 

9.04 was the last version that shipped with myth 0.21, which made my upgrade to it directly from 7.10 + 0.21 backports (skipping 8.04 and 8.10) very simple at the time, using the old-fashioned backup database/wipe/clean install/restore database method. I don't know if 0.22 builds were ever composed for 9.04. If there were in fact 0.22 or 0.23 builds made available for 9.04, it may make the OP's task easier, if he can find them. Canonical only archives distribution-level Mythbuntu, so far as I know.

You're right, I was thinking karmic was 9.04. 9.04 shipped with 0.21 which means the Mythbuntu team provided builds for 0.21 and 0.22. There are 0.22 builds available at [https://launchpad.net/~mythbuntu/+archive/trunk-0.22](https://launchpad.net/~mythbuntu/+archive/trunk-0.22) (don't mind the trunk-0.22 label, these are 0.22+fixes builds). 

In any case, I wouldn't recommended staying on an unsupported version of Ubuntu. I'd recommend upgrading to 10.04

---

### Post by BicyclerBoy on 2011-05-31
The OP questions have not been answered..not that my attempt will..

There is a MythTV frontend package.
You need the version to match your existing setup..
Using mythbuntu may confuse the matter..

Space required:
not sure...

Usability:
SD H264 works okay with the pathetic intel 945GM chipset & intel i915 driver
HD playback is not usable with the above
You need h/w video decode for HD. ION ION2 Fusion ?

Alternative:
mini-PCIe Broadcom CrystalHD is starting to get support in recent MythTV

---

### Post by klc5555 on 2011-06-01
> **BicyclerBoy said:**
> The OP questions have not been answered..not that my attempt will..

There is a MythTV frontend package.
You need the version to match your existing setup..
Using mythbuntu may confuse the matter..

Space required:
not sure...

Usability:
SD H264 works okay with the pathetic intel 945GM chipset & intel i915 driver
HD playback is not usable with the above
You need h/w video decode for HD. ION ION2 Fusion ?

Alternative:
mini-PCIe Broadcom CrystalHD is starting to get support in recent MythTV

As I wrote in my original reply, the OP needs exactly two .deb packages for a remote frontend. These are mythtv-frontend and mythtv-common. Space requirements are just a few Megs.

As also pointed out in the original reply, his main problem will likely be his main mythtv setup is probably later than 0.21. If so, the .debs for myth 0.22 and later will probably not install nor run on his netbook running on Ubuntu 9.04, because of the normal Ubuntu dependency hell; he may have to upgrade the OS from 9.04 to a version compatible with the version of myth he needs to run on the netbook. 

tgm4883 recommended 10.04, and he's right, of course. Unlike 9.04 (or 9.10, if his myth setup is 0.22) 10.04 is still supported and will be for a long time, plus it can run every version of mythtv from 0.24 all the way back to 0.21 (with a little tinkering).

---

### Post by BicyclerBoy on 2011-06-02
Well so you did...

I have the same MythTV version on 10.04, netbook-10.10 & 11.04 but not from Ubuntu repos.
I would not recommend the Ubuntu repos for MythTV.

I have compiled from source on occasion.
I have not had any dependency problems with MythTV..
MySql is the likely candidate for problems on a old system.

I would have recommended an upgrade to netbook 10.10 if it had not been broken (& not fixed).
The 10.10-netbook was actually very good.

---

### Post by tgm4883 on 2011-06-02
> **BicyclerBoy said:**
> 
I would not recommend the Ubuntu repos for MythTV.


Why not?

---

### Post by BicyclerBoy on 2011-06-02
Only for the very reasons klc5555 stated.

Dependencies & the inability to use a  MythTV version of your choice on any (almost) *buntu release.

One additional reason could be the wish to use a more bleeding edge package..

---

### Post by tgm4883 on 2011-06-02
> **BicyclerBoy said:**
> Only for the very reasons klc5555 stated.

Dependencies & the inability to use a  MythTV version of your choice on any (almost) *buntu release.

To answer the first part, what dependency issues? To answer the second, LTS releases will be getting all builds that are compatible with them until the next LTS release (8.04 couldn't because of the new MythUI dependencies). Regular releases get builds for the MythTV version included with the release plus the next major version (see [http://mythbuntu.org/files/mythbuntu-repos.db](http://mythbuntu.org/files/mythbuntu-repos.db))

> **BicyclerBoy said:**
> 
One additional reason could be the wish to use a more bleeding edge package..

Since the Mythbuntu team does builds from the MythTV stable branch & trunk branch every day that there are changes, how can you have a more bleeding edge package?


I'm not arguing to argue. I am close to the daily builds and the packaging in Ubuntu and legitimately want to know what is wrong with them.

---

### Post by BicyclerBoy on 2011-06-03
Well I'm completely wrong then.
You'll know better than me.

As I said the only dependency I can ever recall was MySql5.0 -->5.1 ? & that may have been pre 9.04..klc5555 was talking about dependency hell 

Maybe my out-dated mindset stems from the days of *buntu 8.04 MythTV, which was not usable in my corner...
I do not want to use the mythbuntu builds.

Back to the OP:
I would suggest that 10.04 is a very good release for mythtv. This release has little to find fault & it is LTS.
You can find nvidia driver & mythtv/handbrake/ffmpeg ppas of different versions.
MythTV 0.24+fixes is also well worth a look.

---

### Post by geekyhawkes on 2011-06-03
Thanks for the replies guys.  My netbook is an acer aspire with an 8gb ssd so i dont really want a full mythbuntu setup if i can help it, the poor girl would struggle i think.  Im running mythbuntu 10.10 in my backend so i guess i just need to go up to something like ubuntu 10.04 or better on the netbook then install the packages as listed above.  I will let you know how i get on, i dont mind battling through deendancies if i have to to get this working, better that than an unusable netbook once i close the frontend i guess.

Thanks again

---

### Post by tgm4883 on 2011-06-03
> **BicyclerBoy said:**
> Well I'm completely wrong then.
You'll know better than me.

As I said the only dependency I can ever recall was MySql5.0 -->5.1 ? & that may have been pre 9.04..klc5555 was talking about dependency hell 

Maybe my out-dated mindset stems from the days of *buntu 8.04 MythTV, which was not usable in my corner...
I do not want to use the mythbuntu builds.

Back to the OP:
I would suggest that 10.04 is a very good release for mythtv. This release has little to find fault & it is LTS.
You can find nvidia driver & mythtv/handbrake/ffmpeg ppas of different versions.
MythTV 0.24+fixes is also well worth a look.

When you say you don't want to use the mythbuntu builds, are you talking about the Mythbuntu distrobution, or the Mythbuntu supplied MythTV packages?

---

### Post by geekyhawkes on 2011-06-05
So im getting somewhere / no where!  I have mythtv packages installed on my netbook as described above and the netbook is now running 11.04 (32bit).  When i load the frontend it comes up with the following error;

This version of mythtv requires an updated database (schea is 10versions behind)

Please run mythtv-setup or mythbackend to update your database.


I tried mythtv-setup on the netbook and it isnt installed so im guessing it meant run it on my backend machine.  Thing is where to i upgrade the database?

My backend is 10.10 with the Mythrepositories installed nd configured for myth .24 (so i assume im running myth .24?)  

Thanks for the help.

---

### Post by geekyhawkes on 2011-06-05
Actually i think i might still be running .23;

 grep "mythbackend version:" /var/log/mythtv/mythbackend.log |tail -1
2011-06-05 09:48:19.652 mythbackend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)

So is there an easy way to upgrade to .24 (i hoped adding the updaterepos and selecting myth .24.x woul do that for me).

Thanks

---

### Post by klc5555 on 2011-06-05
Since you have a fully-functioning and stable mythtv setup running 23.1, and since the netbook remote frontend thing is at best an afterthought, I'd recommend altering the netbook to match your mythtv setup rather than altering your mythtv setup to match this netbook. A lot fewer potential headaches.

There are two ways to alter the netbook. The thorough and supported method  would be to blow away completely what the netbook has on it (i.e. 11.04) and install 10.10 and its two 0.23.1 mythtv packages (mythtv-common and mythtv-frontend) 

However, you may wish to leave the netbook OS (and its data) intact. So the unsupported alternative would be to use synaptic and uninstall completely any mythtv packages you may have installed on this netbook. Then download the two 10.10 packages for mythtv-common and mythtv-frontend 0.23.1 from here: [http://packages.ubuntu.com/maverick/graphics/](http://packages.ubuntu.com/maverick/graphics/)

and use your gdebi package installer to install them. (Gdebi may likely claim that two or three dependency packages are also necessary; download and install them as well) 

These slightly older binaries from 10.10 will likely run just fine on 11.04. If they do run, then lock these versions in synaptic so that update manager will not constantly try to upgrade them, and you can get on with business. If it were to turn out, suprisingly, that the older binaries would not run, then you could still do things the supported way by wiping 11.04 completely and installing 10.10 to match your mythtv setup.

---

### Post by geekyhawkes on 2011-06-05
You are probably right, but while I'm getting myth how I want it house wide I'm thinking I should bite the bullet and drive for the most up to date stable version hence going to get the backend up to .24 I think. 

So what's the best way to do that? I thought the auto repos would do that but it appears not. 

Thanks

---

### Post by tgm4883 on 2011-06-05
> **geekyhawkes said:**
> You are probably right, but while I'm getting myth how I want it house wide I'm thinking I should bite the bullet and drive for the most up to date stable version hence going to get the backend up to .24 I think. 

So what's the best way to do that? I thought the auto repos would do that but it appears not. 

Thanks

It depends on what Mythbuntu release you are running. Not all have 0.24 builds for them (although if you are using one that doesn't I recommend upgrading since that means you are on a fairly old build).

Mythbuntu-repos will add the 0.24 repository, but you still have to do the apt-get update and apt-get upgrade

---

### Post by geekyhawkes on 2011-06-06
Thanks for all the help, i decided to bite the bullet and upgraded my backend to 11.04, figured best to get to an lts if im planning on leaving it a standard. 
Front end on the netboook runs pretty well, even on wifi for standard def tv although im planning on using cat5.

The last thing i just need a steer toward is how do i get all the plugins running on my frontend ( thinking mythvideo/mythmusic/mythgame etc) ? 

Thanks again

---

### Post by klc5555 on 2011-06-06
11.04 is not LTS, of course. That was 10.04 and (I suppose) will be 12.04. 11.04 has the same astonishingly short shelf life of any normal interim release. (Oops, sorry. I'm more comfortable in a Slackware world where security fixes still occasionally appear for versions from the late '90s.)

At any rate, to get specific frontend plugins working on your remote frontend (like mythgallery, mythweather, etc.), you'll need to apt-get or use synaptic to download and install the specific plugin package you're looking for, or you can download the particular packages yourself from [http://packages.ubuntu.com/natty/graphics/](http://packages.ubuntu.com/natty/graphics/) and install them using gdebi.

Once a specific frontend plugin package has been installed, its launcher should appear in the expected place on your netbook's myth menu next time you launch mythfrontend.

---

### Post by geekyhawkes on 2011-06-06
Thanks, silly me on the lts, i figured it would be the same as normal ubuntu with the .04 releases being lts. Never mind, right onto getting a fully working frontend in my kitchen! 

Thanks again for all the help guys.

---

