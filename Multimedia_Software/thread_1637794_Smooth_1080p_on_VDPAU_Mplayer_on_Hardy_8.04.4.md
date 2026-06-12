---
title: "Smooth 1080p on VDPAU Mplayer on Hardy 8.04.4"
date: 2010-12-04
forum: Multimedia Software
---

### Post by shreepads on 2010-12-04
I had a problem playing full HD videos (1080p @ 30 fps), frames dropped, CPU utilisation (on 1 of 2 CPUs) maxed out etc.

As I'm still stuck on Hardy I didn't find much stuff that directly answers my question on how to play this... After hunting about a bit the following two links gave me some idea of what needs to be done, namely install a new version of Mplayer that supports VDPAU (NVidia's hardware video acceleration solution).
- [http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)
- [http://kristianlyng.wordpress.com/2009/03/28/vdpau-1080p-with-cpu-cycles-to-spare/](http://kristianlyng.wordpress.com/2009/03/28/vdpau-1080p-with-cpu-cycles-to-spare/)

Luckily I had a NVidia video card that supports VDPAU and I had installed the NVidia proprietary drivers before (details here [http://ubuntuforums.org/showthread.php?t=1544086](http://ubuntuforums.org/showthread.php?t=1544086)).

To check if your NVidia card supports VDPAU please look at the proprietary driver release details. 

Quote from Wikipedia: > "Currently only second generation of PureVideo HD bit-stream processor in some of NVIDIA's GeForce 8 series and later graphics cards hardware that has support since the Beta device driver version 180.06.[4] Unsupported hardware from the GeForce 8 series includes the 8800GTS 320/640MB editions and the 8800GTX. Later cards based on the G9x series cores e.g. the 8400GS and the 8800GTS 512mb (G92 core) are supported."

I usually play using VLC but was put-off from trying to upgrade that to CDPAU support because of this little detail from the Ubuntu forum links above:
> "VLC is available with vdpau by way of VA-API, in this PPA: [https://launchpad.net/~nvidia-vdpau/...dge-multimedia](https://launchpad.net/~nvidia-vdpau/...dge-multimedia)

However, to install it you'll have to upgrade your precious and very touchy ffmpeg packages. There have been a couple of SONAME upgrades since Karmic's ffmpeg was released, and this will inevitably result in breakage of anything that A) uses dynamic ffmpeg, and B) is not rebuilt against the new version, ie. every package that's on your system that didn't come from that PPA."

---

### Post by shreepads on 2010-12-05
OK here's a quick step-by-step of what needs to be done, but first my system specs FYI:

a. Ubuntu 8.04.4 Kernel Linux 2.6.24-28 generic
b. Intel DG33FB motherboard
- Intel G33 Express Chipset
- Intel GMA 3100 onboard graphics card
- One PCI Express x16 connector (PCI Express v1.1): Palit NVidia GT 240 1GB DDR5 Sonic PCIe card (256.53 proprietary driver)
c. Intel C2D E7200 @ 2.53Ghz
d. 2 GB RAM (DDR2)
e. 2 x 3 Gbps SATA drives
f. LG Flatron Wide 19" LCD monitor with DVI-D sockets
g. Corsair 400w PSU

**_Prerequisite:_**

Install the latest NVidia proprietary drivers for your card, check that VDPAU is supported (this has a detailed guide [http://ubuntuforums.org/showthread.php?t=1544086](http://ubuntuforums.org/showthread.php?t=1544086))

**_From an ordinary user login:_**

1. Go to this link ([ftp://download.nvidia.com/XFree86/vdpau/](ftp://download.nvidia.com/XFree86/vdpau/)) and download the latest 'mplayer-vdpau-*.tar.bz2' and 'vdpau-docs-*.tar.bz2). I picked up
-mplayer-vdpau-4789364.tar.bz2
-vdpau-docs-4601358.tar.bz2

2. Extract the files from the two archives, preferably to your ordinary user's home directory. They will create subfolders 'mplayer-vdpau-*' and 'vdpau-docs-*'.

3. Check if your system has a 'usr/include/vdpau' folder, usually this is installed by the NVidia proprietary driver. If not then download the files in the 'include/vdpau' folder at the NVidia FTP link above

**_From an admin user login:_**

1. Create the 'usr/include/vdpau' folder (if it doesn't already exist) and drop the two .h files downloaded from the NVidia site as per step 4 above

2. From the terminal run this
```
$ sudo apt-get build-dep mplayer
```

3. Try this from the terminal (although it didn't work for me)
```
$ sudo apt-get install subversion
```

   Instead I had to open up the Synaptic Package Manager, find 'subversion' and install it from there

4. Just to be on the safe side run Update Manager and check for and install any updates.

**_Back to the ordinary user login:_**

I like this part of this solution, you're assured that you're not messing around with any system files, just doing a local user build. 
No need to use 'su' for anything that follows

1. Open Terminal and go to the 'mplayer-vdpau-*' extract folder e.g.  '/home/user/mplayer-vdpau-4789364'

2. Run the following command
```
  $ sh checkout-patch-build.sh
```

3. If all goes well this should 
[LIST]
[*]Check-out a bunch of source files into a subfolder 'mplayer-vdpau' (e.g. /home/user/mplayer-vdpau-4789364/mplayer-vdpau)
[*]Patch some of them using the *.patch files downloaded
[*]Run a configure program among the source files
[*]Run a make succesfully, but with a bunch of warnings
[/LIST]

4. If all went well you should see an executable 'mplayer' in the 'mplayer-vdpau' subfolder

5. In the terminal navigate to the 'mplayer-vdpau' subfolder and run the following:
```
  $ ./mplayer -vc help > codecs.txt
```
  This should create a codecs.txt file that lists all the codecs you can use with the build, have a look at the ones that include 'vdpau' in their names, these will be the ones to use in the next command.

6. Run the following:
```
  $ ./mplayer -vo vdpau -vc <VDPAU-codec-name> <filename>
```
  For example to open an 1080p H.264 encoded video run
```
  $ ./mplayer -vo vdpau -vc ffh264vdpau <filename>
```

7. Hopefully this will play your videos, but I had a problem with one particular video, specs
> Container			 : MKV
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.1
Codec ID                         : V_MPEG4/ISO/AVC
Bit rate                         : 12.6 Mbps
Width                            : 1 920 pixels
Height                           : 1 080 pixels
Display aspect ratio             : 16:9
Frame rate                       : 23.976 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive

8. After some reading online I figued I needed the latest mplayer/ ffmpeg builds to run this correctly. After several changes to the checkout-patch-build.sh file, build failures, lookups on the mplayet GIT webpage etc I finally created the attached custom checkout-patch-build.sh file that 'just works'...

9. Before running this delete the 'mplayer-vdpau' subfolder created by step 3.

10. Get the list of codecs for the new mplayer using step 5. Then run the attached custom checkout-patch-build.sh file using step 6.

With this new one I was able to get the above-mentioned video playing very smoothly indeed. CPU utilisation < 15% but the NVidia card moved to the performance mode and heated up to 62 deg C. Within a minute of the video stopping the NVidia card was back to desktop mode and the usual 42 deg C temperature.

---

### Post by shreepads on 2010-12-05
Ahh yes with the attachment mentioned in the last post (6th time lucky!!) and marked as solved..

The main differences from the one from the NVidia site:
- Newer versions of mplayer/ ffmpeg/ dvdnav
- The full ffmpeg package needs to be downloaded in a separate subfolder
- No patching reqd as the patch code is already included in mplayer latest releases
- The 'configure' script needs to be run with the "--yasm=''" option as the yasm package in Hardy doesn't work with this script

I have just used the latest SVN version numbers, does anyone have the latest stable release SVN version numbers for mplayer, ffmpeg and dvdnav from the mplayer GIT site?

---

### Post by shreepads on 2011-01-14
Did a fresh install of 64-bit Lucid 10.04.1 LTS. Same hardware as described in the 2nd post above.

Installed the latest 64-bit drivers from NVidia, using a slightly different approach, details here:
[http://ubuntuforums.org/showthread.php?t=1665630](http://ubuntuforums.org/showthread.php?t=1665630)

The above mentioned problematic MKV file couldn't be played in the default mplayer install. VLC was able to play it but with maxed out CPU utilisation and some frames being dropped..

Got it working using the latest mplayer vdpau as described above, but with some small changes
- This Nvidia driver install (260.19.29) didn't create the /usr/include/vdpau folder and files so had to do this step
- Didn't bother to get the mplayer-vdpau and docs files from the NVidia FTP site
- sudo apt-get install subversion worked fine

Then used the same script file attached in the post above to checkout and build the mplayer vdpau version and now the problematic MKV file is playing fine!!

The card seemed to heat up a tad more to 65 deg C, but no other issues...

---

