---
title: "Trying to install libmp4v2-2  -- mythexport fails"
date: 2014-06-11
forum: Mythbuntu
---

### Post by Kerby_Armand on 2014-06-11
[COLOR=#393939][FONT=arial][B]Hi ya'll. I've tried for days. I want to finish a script for HandBrakeCLI and what's missing is the ability to make an mp4/m4v file.
So I figured it 'must' be the missing libmp4
When trying to install it - or any updates lately I get this same error with mythexport.
Any clue as to why>
Mythbuntu 14.04
Thanks for help.
-Scan

Installing package(s) with command apt-get -y --force-yes -f install libmp4v2-2 ..[/B][/FONT][/COLOR]
Setting up mythexport (2.2.4-0ubuntu2) ...
mkdir: missing operand
Try 'mkdir --help' for more information.
dpkg: error processing package mythexport (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  libmp4v2-2
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 417 kB of archives.
After this operation, 1091 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe libmp4v2-2 amd64 2.0.0~dfsg0-2 [417 kB]
Fetched 417 kB in 0s (894 kB/s)
Selecting previously unselected package libmp4v2-2.
(Reading database ... 186029 files and directories currently installed.)
Preparing to unpack .../libmp4v2-2_2.0.0~dfsg0-2_amd64.deb ...
Unpacking libmp4v2-2 (2.0.0~dfsg0-2) ...
Setting up mythexport (2.2.4-0ubuntu2) ...
mkdir: missing operand
Try 'mkdir --help' for more information.
dpkg: error processing package mythexport (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libmp4v2-2 (2.0.0~dfsg0-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by blm-ubunet on 2014-06-11
Forcing packages is a really bad idea unless you know exactly what is the blockage.
It is better to find the exact problem & try to work around.
The package management system does get itself into a cyclical deadlock & removing a couple of packages can then allow you to resolve.

Looking at package dependencies with synaptic package manger:
There is no dependency on libmp4 by HandBrakeCLI.
libmp4 requires certain versions of libc etc.
I am fairly sure HB uses ffmpeg's libav* libraries (system) for all mpeg4.
Might use libxvid for encoding mpeg4-asp (don't use).

IIRC HB uses slightly misleading names like QT quicktime or 3GP for mp4.

Could check if HB loads that lib with:
ldd /usr/bin/HandBrakeCLI

I would guess there is a bug in the post-installation script for the mythexport package.

Looking at mythexport launchpad page:
- there is no intel/amd64 bit build (no big deal)
- there is no i386 build in trusty release
- there is an i386 build in trusty proposed.

You could download mythexport package directly from launchpad or could change package management to use "proposed".

---

### Post by mraggie on 2014-06-11
I am also seeing this issue.  Not sure where in post install the error is occuring.  looks like it is trying to make a directory.

Setting up mythexport (2.2.4-0ubuntu2) ...
Progress: [ 98%]
mkdir: missing operand
Try 'mkdir --help' for more information.
dpkg: error processing package mythexport (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mraggie on 2014-06-11
mythbox@mythbox:/var/lib/dpkg/info$ vi mythexport.postinst

#! /bin/sh -e

reload_apache()
{
    if apache2ctl configtest 2>/dev/null; then
        invoke-rc.d apache2 force-reload || true
    else
        echo "Your apache2 configuration is broken, so we're not restarting it for you."
    fi
}

#Used to fail at some point but not abort postinst
fail_database() {
    echo "Failed to create or modify database (incorrect MySQL username/password?)" >&2
    echo "Verify /etc/mythtv/mysql.txt then try:" >&2
    echo "sudo dpkg-reconfigure mythexport" >&2

    db_input high mythexport/mysql_error || true
    db_set mythexport/password ""
    exit 0
}

case "$1" in
    configure)
    . /usr/share/debconf/confmodule

    db_get mythexport/dir
    dir="$RET"

    if [ -n $dir ]; then
        mkdir -p $dir

        chown mythtv:mythtv $dir || true
        chmod 775 $dir || true

        if [ ! -e /usr/share/mythtv/mythexport/video ]; then
            # remove broken symlink if it exists
            if [ -h /usr/share/mythtv/mythexport/video ]; then
                rm /usr/share/mythtv/mythexport/video
            fi
            ln -s $dir /usr/share/mythtv/mythexport/video
        fi
    fi

    mkdir -p /var/www/.mythtv
    mkdir -p /home/mythtv/.mythtv

    if [ ! -e /var/www/.mythtv/config.xml ]; then
        ln -s /etc/mythtv/config.xml /var/www/.mythtv/config.xml
    fi
    if [ ! -e /home/mythtv/.mythtv/config.xml ]; then
        ln -s /etc/mythtv/config.xml /home/mythtv/.mythtv/config.xml
    fi
"mythexport.postinst" [readonly] 131 lines, 3837 characters

---

### Post by blm-ubunet on 2014-06-12
you could edit script & add
```
**set -x**
```
at the beginning (after the shebang)

Then try running it again in a terminal

---

### Post by Kerby_Armand on 2014-06-12
FYI: [just making notes for reading along]
ldd /usr/bin/HandBrakeCLI
	linux-vdso.so.1 =>  (0x00007fffbcf9f000)
	liba52-0.7.4.so => /usr/lib/x86_64-linux-gnu/liba52-0.7.4.so (0x00007f3832f54000)
	libass.so.4 => /usr/lib/x86_64-linux-gnu/libass.so.4 (0x00007f3832d30000)
	libavcodec.so.54 => /usr/lib/x86_64-linux-gnu/libavcodec.so.54 (0x00007f3831fd9000)
	libavformat.so.54 => /usr/lib/x86_64-linux-gnu/libavformat.so.54 (0x00007f3831cb7000)
	libavutil.so.52 => /usr/lib/x86_64-linux-gnu/libavutil.so.52 (0x00007f3831a92000)
	libavresample.so.1 => /usr/lib/x86_64-linux-gnu/libavresample.so.1 (0x00007f3831875000)
	libdvdnav.so.4 => /usr/lib/x86_64-linux-gnu/libdvdnav.so.4 (0x00007f3831661000)
	libdvdread.so.4 => /usr/lib/x86_64-linux-gnu/libdvdread.so.4 (0x00007f3831444000)
	libmkv.so.0 => /usr/lib/x86_64-linux-gnu/libmkv.so.0 (0x00007f383123b000)
	libmpeg2.so.0 => /usr/lib/x86_64-linux-gnu/libmpeg2.so.0 (0x00007f383101d000)
	libmp3lame.so.0 => /usr/lib/x86_64-linux-gnu/libmp3lame.so.0 (0x00007f3830d90000)
	libsamplerate.so.0 => /usr/lib/x86_64-linux-gnu/libsamplerate.so.0 (0x00007f3830a23000)
	libswscale.so.2 => /usr/lib/x86_64-linux-gnu/libswscale.so.2 (0x00007f38307dc000)
	libtheoraenc.so.1 => /usr/lib/x86_64-linux-gnu/libtheoraenc.so.1 (0x00007f383059c000)
	libtheoradec.so.1 => /usr/lib/x86_64-linux-gnu/libtheoradec.so.1 (0x00007f3830382000)
	libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007f3830155000)
	libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007f382fc86000)
	libx264.so.142 => /usr/lib/x86_64-linux-gnu/libx264.so.142 (0x00007f382f8ef000)
	libbluray.so.1 => /usr/lib/x86_64-linux-gnu/libbluray.so.1 (0x00007f382f6b5000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f382f497000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f382f190000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f382edca000)
	libfribidi.so.0 => /usr/lib/x86_64-linux-gnu/libfribidi.so.0 (0x00007f382ebb3000)
	libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007f382e976000)
	libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007f382e6d3000)
	libenca.so.0 => /usr/lib/x86_64-linux-gnu/libenca.so.0 (0x00007f382e4a0000)
	libxvidcore.so.4 => /usr/lib/x86_64-linux-gnu/libxvidcore.so.4 (0x00007f382e161000)
	libvpx.so.1 => /usr/lib/x86_64-linux-gnu/libvpx.so.1 (0x00007f382dd82000)
	libvo-amrwbenc.so.0 => /usr/lib/x86_64-linux-gnu/libvo-amrwbenc.so.0 (0x00007f382db68000)
	libvo-aacenc.so.0 => /usr/lib/x86_64-linux-gnu/libvo-aacenc.so.0 (0x00007f382d94a000)
	libspeex.so.1 => /usr/lib/x86_64-linux-gnu/libspeex.so.1 (0x00007f382d731000)
	libschroedinger-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libschroedinger-1.0.so.0 (0x00007f382d46d000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f382d253000)
	libopus.so.0 => /usr/lib/x86_64-linux-gnu/libopus.so.0 (0x00007f382d00b000)
	libopenjpeg.so.2 => /usr/lib/x86_64-linux-gnu/libopenjpeg.so.2 (0x00007f382cde9000)
	libopencore-amrwb.so.0 => /usr/lib/x86_64-linux-gnu/libopencore-amrwb.so.0 (0x00007f382cbd4000)
	libopencore-amrnb.so.0 => /usr/lib/x86_64-linux-gnu/libopencore-amrnb.so.0 (0x00007f382c9aa000)
	libgsm.so.1 => /usr/lib/x86_64-linux-gnu/libgsm.so.1 (0x00007f382c79c000)
	libva.so.1 => /usr/lib/x86_64-linux-gnu/libva.so.1 (0x00007f382c585000)
	librtmp.so.0 => /usr/lib/x86_64-linux-gnu/librtmp.so.0 (0x00007f382c36b000)
	libgnutls.so.26 => /usr/lib/x86_64-linux-gnu/libgnutls.so.26 (0x00007f382c0ac000)
	libbz2.so.1.0 => /lib/x86_64-linux-gnu/libbz2.so.1.0 (0x00007f382be9c000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f382bc97000)
	libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007f382ba8e000)
	libxml2.so.2 => /usr/lib/x86_64-linux-gnu/libxml2.so.2 (0x00007f382b727000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f3833179000)
	libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007f382b4fd000)
	libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007f382b2d6000)
	liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007f382b054000)
	libgcrypt.so.11 => /lib/x86_64-linux-gnu/libgcrypt.so.11 (0x00007f382add5000)
	libtasn1.so.6 => /usr/lib/x86_64-linux-gnu/libtasn1.so.6 (0x00007f382abc0000)
	libp11-kit.so.0 => /usr/lib/x86_64-linux-gnu/libp11-kit.so.0 (0x00007f382a97e000)
	liblzma.so.5 => /lib/x86_64-linux-gnu/liblzma.so.5 (0x00007f382a75c000)
	libgpg-error.so.0 => /lib/x86_64-linux-gnu/libgpg-error.so.0 (0x00007f382a556000)
	libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007f382a34e000)

---

### Post by Kerby_Armand on 2014-06-12
Note: Perhaps I am asking the wrong question. If HandBrakeCLI is not using libmp4v; then what is the key for creating a different container for video.
Example:
This works:
HandBrakeCLI -i /Storage/recordings/1281_20140610214800.mpg -o /Storage/recordings/converted.mkv -m -E copy --audio-copy-mask ac3,dts,dtshd --audio-fallback ffac3 -e x264 -q 20 -x level=4.1:ref=4:b-adapt=2:direct=auto:me=umh:subq=8:rc-lookahead=50:psy-rd=1.0,0.15:deblock=-1,-1:vbv-bufsize=30000:vbv-maxrate=40000:slices=4

But If I change the file format of the converted file to mp4 or m4v it fails.
The HandBrake GUI works and creates the file fine.

What am I missing? What is HandBrakeCLI missing or why is it unable to work like HandBrake CUI?

Interesting.
-scan

-I've also tried simple -i -o with less/more complex parameters and making .mkv files work.

---

### Post by Kerby_Armand on 2014-06-12
I noticed this morning there were "updates" available. Many on the list.
So I ran this:


[LIST]**apt-get -y install handbrake-cli **Setting up mythexport (2.2.4-0ubuntu2) ...
mkdir: missing operand
Try 'mkdir --help' for more information.
dpkg: error processing package mythexport (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  gstreamer1.0-libav gstreamer1.0-pulseaudio libjavascriptcoregtk-1.0-0
  libmkv0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  handbrake
The following packages will be upgraded:
  handbrake-cli
1 upgraded, 0 newly installed, 1 to remove and 24 not upgraded.
1 not fully installed or removed.
Need to get 5090 kB of archives.
After this operation, 8130 kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/) trusty/main handbrake-cli amd64 6210svnppa1~trusty1 [5090 kB]
Fetched 5090 kB in 2s (1721 kB/s)
(Reading database ... 186036 files and directories currently installed.)
Removing handbrake (0.9.9+dfsg-2~2.gbpa4c3e9build1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
(Reading database ... 186018 files and directories currently installed.)
Preparing to unpack .../handbrake-cli_6210svnppa1~trusty1_amd64.deb ...
Unpacking handbrake-cli (6210svnppa1~trusty1) over (0.9.9+dfsg-2~2.gbpa4c3e9build1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up mythexport (2.2.4-0ubuntu2) ...
mkdir: missing operand
Try 'mkdir --help' for more information.
dpkg: error processing package mythexport (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up handbrake-cli (6210svnppa1~trusty1) ...
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/LIST]

---

### Post by Kerby_Armand on 2014-06-12
I am also noting that any update on this MythBuntu 14.04 fails with that mythexport mkdir: missing operand error.
I am not able to run an update ( GUI or command line ).

From my view the only package(s) that I've installed extra are:
HandBrake
Disks
Gedit
Psensor
Grsync

I don't see any reason why this should not update.

-Scan.

---

### Post by blm-ubunet on 2014-06-13
The other updates are okay..just mythexport fails..
Use synaptic package manager if you need a GUI tool that works properly.

> The following packages will be REMOVED:
  handbrake
The following packages will be upgraded:
  handbrake-cli
....
Removing handbrake (0.9.9+dfsg-2~2.gbpa4c3e9build1) .
Suggests to me you are trying to pick some components of the extra ppa (JStebbins HandBrake) & still trying to use Handbrake GUI from mainline release..
Its a bad idea to pick & mix related packages from different ppa. 

Did you force that or just install a deb from somewhere?
 
I suggest running these cmds before installing new packages & if update manager popup indicates updates are avail.:
apt-get update
apt-get upgrade


I don't see why mythexport post-install script would be requiring this:
mkdir -p /var/www/.mythtv


An old copy of HandBrake source includes libmp4v2 & appears to be statically linked in my build.
Package built versions will be using many dynamic loaded system libs.

Are you trying to use a unsupported codec/stream in mpeg4 container? Maybe the GUI just silently just fixes the problem.
IIRC The GUI can be made to show the cmd line options used.

---

### Post by Kerby_Armand on 2014-06-13
Thanks: Reply to BLM,
No force on the install of HandBrakeCLI
I did have to use a different repository and no I did not know mixing them is a problem.
No, I do not see a way the GUI tool shows me the command it's using - wish it did.
I am removing both applications and starting over.
Even when removing the HandBrakeCLI - the error comes up about mythexport.
That one is a little demon that won't go away for some reason. Why would it even try to install the thing when I am removing a different application? Weird.
I'll play with this alittle each morning before work - hence my replies are only in the am.

Thanks for the heads up on a few things; trying to reinstall one at a time again.
How do I get that other ppa out of there? I followed someone's instructions on using it to add HandBrakeCLI - it was the only way I could find the package to install it?
Is there a different one that Ubuntu likes? The regular install from scratch does not have it.

k

---

### Post by Kerby_Armand on 2014-06-13
I was 'better off before' doing this. At least before I had HandBrakeCLI working.
I removed the HandBrakeCLI and HandBrake (gui) apps.
I used the Official Ubuntu Software manager and clicked install on HandBrake.
No go.
The demon showed up.
--------------------------------------------------------------------------------
(Reading database ... 185962 files and directories currently installed.)
Preparing to unpack .../libmkv0_0.6.5.1-1ubuntu1_amd64.deb ...
Unpacking libmkv0:amd64 (0.6.5.1-1ubuntu1) ...
Selecting previously unselected package libjavascriptcoregtk-1.0-0:amd64.
Preparing to unpack .../libjavascriptcoregtk-1.0-0_2.4.2-1ubuntu0.1_amd64.deb ...
Unpacking libjavascriptcoregtk-1.0-0:amd64 (2.4.2-1ubuntu0.1) ...
Selecting previously unselected package libwebkitgtk-1.0-common.
Preparing to unpack .../libwebkitgtk-1.0-common_2.4.2-1ubuntu0.1_all.deb ...
Unpacking libwebkitgtk-1.0-common (2.4.2-1ubuntu0.1) ...
Selecting previously unselected package libwebkitgtk-1.0-0:amd64.
Preparing to unpack .../libwebkitgtk-1.0-0_2.4.2-1ubuntu0.1_amd64.deb ...
Unpacking libwebkitgtk-1.0-0:amd64 (2.4.2-1ubuntu0.1) ...
Selecting previously unselected package handbrake.
Preparing to unpack .../handbrake_0.9.9+dfsg-2~2.gbpa4c3e9build1_amd64.deb ...
Unpacking handbrake (0.9.9+dfsg-2~2.gbpa4c3e9build1) ...
Selecting previously unselected package gstreamer1.0-libav:amd64.
Preparing to unpack .../gstreamer1.0-libav_1.2.4-1~ubuntu1_amd64.deb ...
Unpacking gstreamer1.0-libav:amd64 (1.2.4-1~ubuntu1) ...
Selecting previously unselected package gstreamer1.0-pulseaudio:amd64.
Preparing to unpack .../gstreamer1.0-pulseaudio_1.2.4-1~ubuntu1_amd64.deb ...
Unpacking gstreamer1.0-pulseaudio:amd64 (1.2.4-1~ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up mythexport (2.2.4-0ubuntu2) ...
mkdir: missing operand
Try 'mkdir --help' for more information.
dpkg: error processing package mythexport (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libmkv0:amd64 (0.6.5.1-1ubuntu1) ...
Setting up libjavascriptcoregtk-1.0-0:amd64 (2.4.2-1ubuntu0.1) ...
Setting up libwebkitgtk-1.0-common (2.4.2-1ubuntu0.1) ...
Setting up libwebkitgtk-1.0-0:amd64 (2.4.2-1ubuntu0.1) ...
Setting up handbrake (0.9.9+dfsg-2~2.gbpa4c3e9build1) ...
Setting up gstreamer1.0-libav:amd64 (1.2.4-1~ubuntu1) ...
Setting up gstreamer1.0-pulseaudio:amd64 (1.2.4-1~ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Errors were encountered while processing:
 mythexport
Error in function: 
Setting up mythexport (2.2.4-0ubuntu2) ...
mkdir: missing operand
Try 'mkdir --help' for more information.
dpkg: error processing package mythexport (--configure):
 subprocess installed post-installation script returned error exit status 1

---

### Post by blm-ubunet on 2014-06-13
I would not use the software centre for anything.
Install synaptic package manager.

There should not be a problem with Mr Stebbins's HandBrake ppa if you let it install all dependencies.
It should not mess up system libs.
It might replace some with more complete ones.
It could be broken at times.
Could have new features & fixes missing in mainline.

There are differences between the complete (extra uncut) versions of important libraries & those shipped by default.
The libav* libraries are a good example of this.

There is a tool callled "ppa-purge" to help get rid of stuff installed from a ppa.

Using synaptic:
To remove a ppa manually, you first need to select-mark-remove the packages from the ppa & only then remove the ppa entry.

Mythexport:
The package management system remembers/knows the package mythexport is not configured. It will continue to try to complete this forever (until fixed or removed).

You could just try to create the directories listed in the script (with the correct permissions/owners/groups). Then it might just work.

---

### Post by Kerby_Armand on 2014-06-15
OK, I hate it when I fixed it but can't explain how.
It has to be 'what' version is installed.
So, here is what I did.
I removed [COLOR=#000000]the extra ppa (JStebbins HandBrake)
[/COLOR]I removed the mythexport deal. When I did that I updated and the update 'took' without that mythexport issue.
Then I installed HandBrake GUI - just to see what it does.
It was from the Ubuntu sanctioned list. It does not make mp4/m4v s.
This thread and that information gave me the clue that Ubuntu does not ship with it because of ownership issues.
So I removed that version too.
Since my goal was to use HandBrakeCLI I decided to make active [COLOR=#000000]the extra ppa (JStebbins HandBrake) and
[/COLOR]I installed via command line handbrake-cli only.
I ran the simplest of conversions:
HandBrakeCLI -i bbS04E06.mpg -o test5.m4v --preset=“AppleTV 3”

JOY.

Now I have an updated system, new kernel, new libs and I can continue on with this script.
I want to finish a user job that will convert this .mpg MythTV recording to a smaller/compressed version that plays on most platforms. I am doing this after Mythicallibrarian. My test is before that or after that. Then a cron job runs and backs it up. After that who knows. Clean the condo.

Thank you all. Sorry I've not been much help. I don't use forums too much.

---

### Post by Kerby_Armand on 2015-01-26
I am going to update my post: I solved making HandBrakeCLI work and produced a script to add to mythicalLibrarian to catalog recordings, make them human readable, maintain them in the mythtv DB and convert them to a smaller size. I think I'll post my script and how I did it in another thread since I've built two of these boxes now - with two different sets of hardware and the results are the same. Look for a new thread soon called mythicalLibrarian and HandBrakeCLI or something similar.

Thanks for the help and discussion - I don't get to post or read regularly (I work)(A lot) and enjoy sharing when I can.

K

---

