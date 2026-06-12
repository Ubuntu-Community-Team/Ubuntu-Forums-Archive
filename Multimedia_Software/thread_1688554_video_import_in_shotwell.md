---
title: "video import in shotwell?"
date: 2011-02-15
forum: Multimedia Software
---

### Post by northwestuntu on 2011-02-15
is there a way to import video in shotwell photo manager? i had that option with Gthumb but can't find it in shotwell?

i have hd .mts files i would like to import.  i know i can also just browse the card and take them off manually.

---

### Post by slambrick on 2011-04-05
WOW this must be a bigger problem than I thought. Not one reply in nearly 2 months, not good.
I also would like to know about this. I like many other have a digital Camera (Panasonic Lumix fz35) which records video in AVCHD LITE format (not that uncommon these days) but Shotwell does not recognize them. As expected I can of course manually copy them from my SD card but i would like to be able to tag and catalogue them within Shotwell. The Shotwell page suggests that it can import some video formats but I see no way of achieving this.
Does anyone have any suggestions?
I'm using Shotwell 0.9.1 and Ubuntu 10.10

---

### Post by PZJM on 2011-04-13
I have a Kodak Playsport and had the same issue.  The file format for the Playsport is .mov.  At first, I did not notice the videos but after restarting Shotwell they showed up.  Also, I've been upgrading Shotwell on a regular bases.  If you don't have the current copy you may want to check their site and see what version you are running as compared to what Ubuntu installs by default.  I know of some added functionality with the upgrades (ex. email).

---

### Post by eric-yorba on 2011-04-13
Shotwell has had video support since version 0.8.  If the videos aren't recognized on your camera within Shotwell, that's probably either a bug in Shotwell or a bug in GPhoto.  (You're welcome to file a bug with us and we'll look into it.)

That said, you can always drag photos and videos in Nautilus right into Shotwell, and it will import them.

---

### Post by jfaberna on 2011-04-14
I have a Nikon Coolpix S6000 and I had a couple of problems with it; video and photo. I had 2 photos and 2 videos on the camera. At first Shotwell didn't see but 1 photo. The second time I ran it, it recognized the 2 photos and knew that one was a duplicate.  It didn't see the videos.  I closed Shotwell and tired to open the Nikon like a USB flash drive to drag the MOVs off the camera, but seemed to generate errors. I finally got the movie player associated with the camera and could play the videos. Now if I double click the camera on the desktop, it goes directly to  Movie player. I can still open the camera with shotwell by right-clicking and select open with shotwell.

How do I just treat the camera as a memory device?

---

### Post by jfaberna on 2011-04-14
Well, I may have stumbled on to something. I changed the file managers options to allow viewing the camera as just another storage device. With Nautilus file manager open, I went to Edit-> Preferences -> Media and changed Photos to Open Folder and Other Media/Action to open folder.

Now when I plug in the camera, I get the file manager pop-up with the DCIM folder visable and a colored bar with a warning, "The media contains digital photos" with a button to open Shotwell.  SO for photos I click the SHotwell button, and for Movies I work with the File Manager to move the MOV files in.

Not ideal, but a workaround.

---

### Post by RJQ on 2011-04-14
If you guys are using the version in the repos that would be the problem, go to the webpage of Shotwell and install it from their ppa, their latest version for ubuntu lucid can see and download video. good luck.:D

---

### Post by jfaberna on 2011-04-16
So if I want to install Shotwell from their website, should I uninstall the one from the Ubuntu 10.10 Maverick distro first?

What happens with the Software update process after I install the Shotwell from their website.  Will I have to make sure the update process doesn't try to update my Shotwell from the distro update sites?

Jim

---

### Post by jfaberna on 2011-04-16
I was too curious to wait for a reply. 

I uninstalled the shotwell that came with Ubuntu 10.10 (0.7.2) and installed 0.9.2 from their website. It does indeed import photos and videos no matter which order they are shot on the camera. Or at least on my Nikon Coolpix S6000.  Instructions I found on the website, worked as listed, repeated below:

$ sudo add-apt-repository ppa:yorba/ppa
$ sudo apt-get update
$ sudo apt-get install shotwell 

Jim A

---

### Post by andyrays on 2011-06-25
You do NOT have to uninstall the shotwell version from the Ubuntu repositories first. After doing the
   $ sudo add-apt-repository ppa:yorba/ppa
   $ sudo apt-get update
steps it will simply treat the shotwell version in the new repository as an update and upgrade (i.e. replace) your current installed version.

Exactly what I needed, include the videos in the import. If only I could rename the files to a custom name while doing so?

---

### Post by gitano on 2011-08-30
my dad is  using 11.04, and has a nikon coolpix l20 (shoots vids in .avi)

he just noticed that shotwell was not pulling his videos.

i found this: [http://www.omgubuntu.co.uk/2011/08/shotwell-0-11-testing-call/](http://www.omgubuntu.co.uk/2011/08/shotwell-0-11-testing-call/)

basically  its the instructions for building 0.11.0 + trunk

(never built anything before)

anyway it picks up the .avis no problem.  the hard core might not think this is a good fix, but, its working. also i might be violating some rule unknown to me about test builds. i don't know.

(with all the crappy changes to ubuntu i dont think anyone cares anyway)

but now shotwell imports the videos right into the same folder along with
the photos



How to test Shotwell 0.11

The Shotwell repository is hosted on ‘git’. This means you need to either install the ‘git‘ package from the Ubuntu Software Centre to ‘pull’ the source code.

With Git installed run the following command in a new Terminal session: -

    git clone git://git.yorba.org/shotwell

Next up we need to install the dependencies for Shotwell. We’ll do this via the Terminal for simplicities sake: -

    sudo apt-get install libgconf2-dev libgee-dev libgexiv2-dev libglib2.0-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libgtk2.0-dev libgudev-1.0-dev libexif-dev libgphoto2-2-dev libraw-dev libsoup2.4-dev libxml2-dev libsqlite3-dev m4 libunique-dev libwebkit-dev valac libjson-glib-dev

If you’re using Ubuntu 10.10 you will also need to add the Vala PPA @ launchpad.net/~vala-team/+archive/ppa

With everything installed and code pulled it’s time to build.

Head back to the Terminal and enter the following commands one at a time, hitting the return/enter key after each: -

    cd
    cd shotwell/
    ./configure
    make

Now prepare for a bit of a wait – this bit can take a while…

Once all done you can launch Shotwell 0.11 by running: -

    ./shotwell

To install Shotwell 0.11 system wide (for full integration) run: -

    sudo make install

Report bugs encountered at redmine.yorba.org/projects/shotwell/issues

Thanks to Akshat

---

