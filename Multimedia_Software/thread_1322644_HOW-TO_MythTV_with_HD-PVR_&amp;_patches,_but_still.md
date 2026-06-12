---
title: "HOW-TO: MythTV with HD-PVR &amp; patches, but still need some help."
date: 2009-11-11
forum: Multimedia Software
---

### Post by shoeman22 on 2009-11-11
I recently purchased a [HD-PVR]("http://www.hauppauge.com/site/products/data_hdpvr.html") with the intent of using it with my Motorola DCH-3416 cable box, NVIDIA onboard HDMI (w/ audio) and MythTV 0.22 running on Karmic 64bit.  It's been a battle and I still have a few questions, but I do have a working install now so I figured I'd share what worked for me. 

** 1) Getting HDMI audio to work.**
First off, to get the HDMI audio working, I needed to upgrade the ALSA version from 1.0.20 to 1.0.21.  Thankfully, there is an easy to use script provided by soundcheck that takes care of everything for you.  Here's the [post]("http://ubuntuforums.org/showthread.php?p=6589810") I got the script from.  To upgrade ALSA all you need to do is:
[LIST=1]
[*]1. download the script and save it somewhere
[*]2. cd <your-download-dir>
[*]3. tar xvf AlsaUpgrade-1.0.21-3.tar
[*]4. sudo ./AlsaUpgrade-1.0.21-4.sh -di
[*]5. sudo shutdown -r 0
[/LIST]

Then when the restart is complete, you should run:
```
cat /proc/asound/version
```
to make sure the upgrade went ok.  If all went well it should look similar to:
```

Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Nov  8 2009 for kernel 2.6.31-14-generic (SMP).
```

If it says 1.0.21 you're in business.  Now you need to setup a config file for ALSA to deal with the HDMI audio properly.  Just **copy the asound.conf file to /etc/asound.conf** and **reboot**.

The last thing you need to do for sound is to make sure the proper channels are unmuted.  I know there's a command line way to do this, but I liked using the graphical mixer, so I installed gnome-alsa-mixer like so:
```
sudo apt-get install gnome-alsamixer
```
Then go to Applications > Sound & Video and open GNOME ALSA Mixer.

Once it's open, make sure all of the IEC598 boxes are checked (should be 3 of them) and make sure the volume levels are not muted.  For me, I have Master, PCM, Front, Surround, Center, LFE, Side, and hdmi_vol all at about 100%.

You can test that your stuff is working by using speaker-test like so:
```
speaker-test
```

You should hear static out of your front left speaker if all went well.  If you're running into problems, check out soundcheck's [original post]("http://ubuntuforums.org/showthread.php?p=6589810") as there are a few other things you can try.

**2) Install latest NVIDIA drivers for VDPAU**
I've been using avenard.org as my repo because the guy also provides an updated-nightly myth package that works against the 190 nvidia driver versions (ubuntu's mythtv needs 185) and he sometimes applies useful patches that haven't been accepted yet into trunk.  Here's the home page for the repo is [here]("http://avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html").

To add the repo and install the drivers:
[LIST=1]
[*]1. wget [http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key](http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key) && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key
[*]2. echo "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) karmic release" | sudo tee /etc/apt/sources.list.d/avenard.list
[*]3. sudo apt-get update
[*]4. sudo apt-get install nvidia-glx-190 nvidia-190-libvdpau nvidia-190-modaliases nvidia-settings
[*]5. sudo shutdown -r 0
[/LIST]

Now that the driver is installed, you need to run the initial setup for nvidia like so:
```
sudo nvidia-settings
```
This creates /etc/X11/xorg.conf file.  I was running into some screen tearing issues on playback, so I had to modify the file a little by adding:
```
Section "Extensions"
          Option "Composite" "Disable"
EndSection
```
at the very end of the file.  If you do this, you also want to get rid of the splash screen or else it will show an ugly grey box when you login in.  To do that you need to go into both **/etc/gdm/Init/Default** and **/etc/gdm/PreSession/Default** and comment out the following lines:
```
if [ -x '/usr/bin/xsplash' ];
then
/usr/bin/xsplash --gdm-session --daemon
fi
```

The reference post from the XBMC forums is [here]("http://xbmc.org/forum/showthread.php?t=60422").

At this point, I'd do another reboot just to test and make sure it's looking ok, but it's up to you.

**3) Installing MythTV from source.**
If you don't need HD-PVR support, you can probably just use the repo to do the install (ie apt-get install mythtv).  If you do have an HD-PVR though, you'll want to do the compile yourself so you can add 3 patches to keep the system from crashing on channel changes.

First we need to install the dependencies for compiling.  apt-get makes this really easy:
```
sudo apt-get build-dep mythtv
```

Now let's grab the source for myth, I grabbed the .22 fixes branch from svn.mythtv.org.  If you're more adventurous you could grab trunk, but it's not recommended.  Make sure subversion is installed.  If it's not, run:```
sudo apt-get install subversion
```.

Once you have subversion, checkout a copy of the stable fixes branch.  I like to use /usr/local/src as a place for the source but it's your call:
```
svn co http://svn.mythtv.org/svn/branches/release-0-22-fixes mythtv_0-22-fixes
```

Now we need to do some patching to make HD-PVR useful, so copy the *.patch and *.diff files into the mythtv_0-22-fixes/mythtv/ folder ,then run:
```
patch --dry-run -p0 -i channel-thread-v1.4a.patch
patch -p0 -i channel-thread-v1.4a.patch
patch --dry-run -p0 -i hdpvr-signalmonitor-v2.patch
patch -p0 -i hdpvr-signalmonitor-v2.patch
patch --dry-run -p0 -i ringbuffer_reset_v2.diff
patch -p0 -i ringbuffer_reset_v2.diff
```

Make sure the dry-run's don't have any conflicts.  I didn't have any with the 22787 revision I'm using right now.

Now we're ready to try and compile it:
```
cd /usr/local/src/mythtv_0-22-fixes/mythtv
./configure --enable-vdpau
make -j2
make install
```
If you only have a one core processor, change "make -j2" to just "make".  If you have a quad core, go with make -j4.  -j just tells make how many cores to use while running make, so the more the faster it will finish.

Now build the plugins:
```

cd /usr/local/src/mythtv_0-22-fixes/mythplugins
./configure
qmake mythplugins.pro
make
sudo make install

```

And the themes:
If you want to build the plugins:
```

cd /usr/local/src/mythtv_0-22-fixes/myththemes
./configure
sudo make install

```


**4) Setup mysql db for myth**
If all went well, it's time to setup the mysql db.
Just run:
```
mysql -uroot -pmypassword < database/mc.sql
mysql -uroot -pmypassword
mysql> grant all on mythconverg.* to mythtv@"%" identified by "mythtv";
mysql> flush privileges;
mysql> exit;
```

[B]5) Get schedules direct account for programming data.
If you want channel listings, you need to subscribe to schedules direct.  It's $20 a year and gives you full programming guide information.  Go to [www.schedulesdirect.com]("http://www.schedulesdirect.org") and get an account setup for use in the backend setup.

**6) Install script for changing channels via firewire:**
Copy 6200ch and 6200ch_wrapper to /usr/local/bin/ and make sure they are executable (sudo chmod a+x /usr/local/bin/6200*).  The 3416 can change channels just fine with the 6200ch script, but my model was being excluded previously.  The wrapper script adds a 1 second pause at the end of the channel change which seemed to help out quite a bit with stability on channel change. It seems obvious to note that you need to connect a firewire cable from the cable box to your computer for this to work, but I'll mention it.

There's also a couple other things to check to make sure firewire is active on your computer.
```
lsmod | grep 1394
dv1394                 21096  0
raw1394                29096  0
ohci1394               33780  1 dv1394
ieee1394              100896  3 dv1394,raw1394,ohci1394
```
should look something like this

If any of those entries are missing, you need to edit /etc/modules and add those lines to it.  here's what my /etc/modules looks like:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
lp
rtc
dv1394
raw1394
ohci1394
ieee1394
```

then reboot and check lsmod | grep 1394 and make sure they are loaded.

After you can confirm that firewire is working, you can actually test if you can change channels by running 
```
6200ch_wrapper <channel_number>
```
If you switched to the proper channel, this is working fine.

**5) Configure myth backend**:
From your desktop, hit alt-f2 and then type "gksudo mythtv-setup" and this will 

launch your backend configuration after you type in your password.  Go to capture devices and select the X.264 encoding device from the top and select the video and audio inputs you are using.  I'm using component and spdif personally.  Click through the remaining screens and hit finish.

Now go to video sources and add a new one.  I named mine cableone_digital.  Input your schedules direct username/pass and then retrieve listings.  If you have multiple sources from schedules direct (ie basic cable vs digital cable in my set up), you'll need to pick which listing to use in the list that's returned.  Click through to finished.

Now go to input sources and add a new one on which ever video input you're using (component for me).  Select which ever schedules direct package ties to that source (cableone_digital for me), then for the channel changing script put in "6200ch_wrapper " (note the white space at the end.  I'm not sure if this is necessary or not, but it works for me).  click through to finish and you're all setup.

Next go to Storage Directories and point those wherever you want.  /var/lib/myth/ is the default location with folders for all the items there (ie recordings, livetv, etc.).

Once you do that, you can exit out of the backend with ESC.

**6) Run mythfilldatabase from the terminal to update the channel guide.**
```
mythfilldatabase
```

**7) Restart the backend. **
```
mythbackend
```

**8) On to the frontend.**
Now that the backend is setup and running, we can tackle the front end.  From the desktop, alt-f2, then type mythfrontend into the prompt and open it up.

Go to setup > tv settings > playback and click through to the playback type page and select the VDPAU Normal profile.  I have the onboard 8300 card I believe and that's as high as I can go.  If you have a better nvidia card, go for VDPAU High.

Check out tv and see if it's working.

If you have any questions let me know.  This is my first myth install, so it may not be the best way to do the patching and compiling.  I'd really like to be able to just patch the mythtv source from the repo, then just let the repo proceed with installing my slightly patched version, but I'm not sure how to simulate that.  As such, this method doesn't include any of the upstart jobs or menu entries which is a pain.  

Does anyone know how to do something like that?  I'd also like to learn how to apply patches with dpatch instead of directly to the source with patch which makes for odness when I svn up the source potentially.  If anyone can help with that too, I'd be very appreciative.

---

### Post by jjuzwik on 2009-12-08
Thanks for the write up!  I did follow this, and it worked great...  Right up until some new security updates were released:(  I should have ignored them.  Now, mythfrontend wont open as it thinks i don't have any themes.  mythtv-setup is also unable to open.

Is there any chance you ran into this?

I was running the vanilla mythbuntu 9.10 install.  Then i compiled and ran the fixes from SVN.  Then i let ubuntu install some typical security updates...  At which point it broke the themes.  Trying different themes manually doesn't fix it either.

I'd much appreciate any pointers.  Thanks!

---

### Post by shoeman22 on 2009-12-08
I would try to do a full recompile of mythtv again and see if that helps.

To do that, go to your source directory and run ```
cd /usr/local/src/mythtv_0-22-fixes
make clean
```

You might also want to pull in any new updates that have been posted to the fixes branch as well by running
```
svn up
``` in that directory before doing the recompile steps again (starting with ./configure --enable-vdpau through the install of the themes and plugins).

Skip the patching steps as they should already be in there.

I'm going to be trying that myself this afternoon after I install the linux headers stuff dist-upgrade wants to bring in, so I'll see how it goes for me and if I run into anything, I'll post back here too.

---

### Post by jjuzwik on 2009-12-08
Thanks for helping out...  But no luck on the recompile:(  I get the same theme related issue trying to open mythfrontend and mythtv-setup.

I did update to the latest SVN, and interestingly enough, the newer version i supposedly installed, isn't the same version i get when i run:

```
$ mythbackend --help
mythbackend version: branches/release-0-22-fixes [22952] www.mythtv.org
```

and...

```
$ svn up
At revision 22968.
```

Its almost as if my builds arent even installing in the right place or something.


Any luck with your updates?

---

### Post by shoeman22 on 2009-12-08
I haven't gotten to it yet, but that version issue makes me wonder if it's referencing the right location

what does 
```
which mythbackend
```

give you?.  By default when you compile the myth* executables are installed at /usr/local/bin ... if somehow the apt-get installed version is hanging around somewhere, it'd be at /usr/bin.

---

### Post by jjuzwik on 2009-12-08
Sure enough:

```
$ which mythbackend
/usr/bin/mythbackend
```

It appears that i am still stuck in the apt-get version...

Should i remove the existing packages?  (keep in mind this is my master backend):-?

Or would it be safe to change the install prefix and recompile?

Either way, i am backing up the DB right now!

---

### Post by shoeman22 on 2009-12-09
You could do it with the prefix, or you could try starting myth with the full path and see if that works.  So you'd start mythbackend with ```
/usr/local/bin/mythbackend
```

Same goes for starting the frontend ```
/usr/local/bin/mythfrontend
```

---

### Post by shoeman22 on 2009-12-09
I missed the question on the existing packages.  

I did a apt-get purge for all the myth* packages when I did it.  I just wanted to make sure nothing collided, but I'm not sure if it's absolutely necessary.  If you have the db backed up though, you should be fine to do it and it might make things cleaner (ie you'd for sure be able to just use mythbackend to start the server rather than have to use the full path.

---

### Post by jjuzwik on 2009-12-10
I did try running with the absolute path, and it made no difference.

I finally took the easy way out, i rebuilt the box, and re-imported my important stuff.  I will probably end up re-compiling, and applying the patches, and NOT install any distro updates until these patches get committed to mytht.22-fixes.  Hopefully that will be sooner rather then later...

Thanks for the help!  

Its a great guide to getting the hd-pvr up and running.

---

