---
title: "Can't make MPD stream MP3 through IceCast2"
date: 2010-02-04
forum: Multimedia Software
---

### Post by Zat3r on 2010-02-04
I have downloaded the MPoD app for iPhone because I wanted a media remote that works with a linux mediaplayer (can't believe I actually found one!) and it works fine. It also has the feature to receive a stream from mpd and play it on the iPhone which seems quite cool. The problem is that i can't set up the MPD to stream mp3 through icecast. The iPhone obviously can't play OGG since it's Apple.

I configured the audio_output lite this:

```

audio_output {
	type		"shout"
	encoding	"mp3"			# optional
	name		"MP3 Shout"
	host		"localhost"
	port		"8000"
	mount		"/mpd.mp3"
	password	"hackme"
#	quality		"5.0"
	bitrate		"128"
	format		"44100:16:2"
	protocol	"icecast2"		# optional
	user		"source"		# optional
	description	"My Stream Description"	# optional
	genre		"jazz"			# optional
	public		"no"			# optional
	timeout		"2"			# optional
}

```

And when i restart MPD I get:

```

$ sudo /etc/init.d/mpd restart
 * Stopping Music Player Daemon mpd                                                                                                                                          [ OK ] 
 * Starting Music Player Daemon mpd                                                                                                                                                 output: line 200: couldn't find shout encoder plugin "mp3"
Aborted

```

Since it's MPD that dies from lack of mp3-support I decided to compile it myself but I still get the same error. Here is the ./configure output:

```

########### MPD CONFIGURATION ############

 Client Support:
 IPv6 support ..................enabled
 TCP support ...................enabled
 Unix domain socket support ....enabled

 Playback Support:
 ALSA support ..................enabled
 FIFO support ..................enabled
 HTTP daemon support ...........enabled
 JACK support ..................disabled
 libao support .................disabled
 OSS support ...................enabled
 OS X support ..................disabled
 Pipeline output support .......disabled
 PulseAudio support ............disabled
 Media MVP support .............disabled
 SHOUTcast support .............enabled
 Solaris /dev/audio support ....disabled

 Streaming Encoder Support:
 LAME mp3 encoder ..............enabled
 Ogg Vorbis encoder ............enabled

 File Format Support:
 AAC support ...................disabled
 C64 SID support ...............disabled
 FFMPEG support ................disabled
 FLAC support ..................disabled
 fluidsynth MIDI support .......disabled
 MikMod support ................disabled
 MODPLUG support ...............disabled
 MAD mp3 decoder support .......enabled
 MP4 support ...................disabled
 Musepack (MPC) support ........disabled
 OggFLAC support ...............disabled
 Ogg Vorbis support ............enabled
   using tremor.................no
 Wave file support .............disabled
 WavPack support ...............disabled
 wildmidi MIDI support .........disabled

 Archive support:
 BZ2 archives support ..........disabled
 ISO 9660 archives support .....disabled
 ZIP archives support ..........disabled

 Streaming support:
 last.fm radio support .........disabled
 libcurl support (streaming) ...enabled
 libmms support ................disabled

 Other features:
 ID3 tag support ...............disabled
 libsamplerate support .........disabled
 Zeroconf support ..............disabled
 libcue support ................disabled

##########################################


```


Any ideas would be appreciated.

---

### Post by MetalMusicAddict on 2010-02-04
Just a note, I'm using streaming output directly through MPD now. (on Karmic)

Here's how.

In a terminal:
```
sudo apt-get build-dep mpd && apt-get source mpd
```

This will install the build-depends as well as download and extract the source archive for the ubuntu .deb.

Go into the extracted source dir and go into the debian/rules file.
You want the 'DEB_CONFIGURE_USER_FLAGS' bit to say:
```
DEB_CONFIGURE_USER_FLAGS += $(WITH_TREMOR) --enable-sqlite --enable-un --enable-ao **--enable-lame-encoder**
```
Update for Maverick. (note the end)
```
DEB_CONFIGURE_USER_FLAGS += $(WITH_TREMOR) --enable-sqlite --enable-un --enable-ao **--enable-lame**
```

*Side note*: While cd'd into mpd's extracted source folder, doing a "./configure --help" will show you all kinds of other options you can add/remove.

Then back in the root dir of the source folder do:
```
debuild binary
```

That should build you the same .deb you get from the repos but with .mp3 output enabled.

My /etc/mpd.conf bit for streaming looks like: 

```
#
audio_output {
        type            "httpd"
        name            "MetalMusicAddict's Jukebox"
        encoder         "lame"                  # optional, vorbis or lame
        port            "8000"
        quality         "6.0"                   # do not define if bitrate is defined
#       bitrate         "192"                   # do not define if quality is defined
        format          "44100:16:2"
}
#
```

If you try this make sure to turn off IceCast and pin your compiled package in Synaptic.

---

### Post by Zat3r on 2010-02-04
I didn't get the httpd output to work. But the icecast did :D So at least it's working now. Thanks a lot! :D

---

### Post by unimatrix on 2010-02-07
Thank you MetalMusicAddict! This helped me a lot. I wanted to stream to a SHOUTCast server, but it would only accept mp3. Your solution worked like a charm!

---

### Post by MetalMusicAddict on 2010-02-07
> **unimatrix said:**
> Thank you MetalMusicAddict! This helped me a lot. I wanted to stream to a SHOUTCast server, but it would only accept mp3. Your solution worked like a charm!

np. For anyone else reading there's a good bit of packages we have that have the non-free bits turned off. (ie: FFMPEG) The above method can be used to recompile them. Just enable the right switches. :)

---

### Post by kevinanchi on 2010-09-04
Hey guys thanks for the information, as we are all under some [Umbrella]("http://www.patio-umbrellas.com"), here are my few cents :)

**Configure MPD to be an Icecast Source**

 Edit /etc/mpd.conf and enable the Icecast audio_output by adding the following: 
 audio_output {
    type        "shout"
    encoding    "ogg"
    name        "my cool stream"
    host        "localhost"
    port        "8000"
    mount       "/mpd.ogg"

# This is the source password in icecast.xml
    password    "hackme"

# Set either quality or bitrate
#   quality     "5.0"
    bitrate     "64"

    format      "44100:16:1"

# Optional Paramters
    user        "source"
#   description "here's my long description"
#   genre       "jazz"
} # end of audio_output

# Need this so that mpd still works if icecast is not running
audio_output {
    type "alsa"
    name "fake out"
    driver "null"
}

---

### Post by durand on 2010-11-07
Thanks MetalMusicAddict, streaming to my android via MPDroid works perfectly now :)

---

### Post by ikonitas on 2010-11-18
Hello,

[MetalMusicAddict]("http://ubuntuforums.org/member.php?u=6176") I just did everything what is in your tutorial I am using ubuntu 10.10 ,

I am getting this error message : ```
output: line 221: No such encoder: lame
```

My mpd.conf

```
# An example of a httpd output (built-in HTTP streaming server):
#
audio_output {
    type         "httpd"
    name       "My HTTP Stream"
    encoder    "lame"        # optional, vorbis or lame
    port          "8000"
    quality      "5.0"            # do not define if bitrate is defined
#    bitrate     "128"            # do not define if quality is defined
    format        "44100:16:1"
}
```

before that I was building **.DEB **file in the end I got some warrnings : 

```
dpkg-deb: warning: 'debian/mpd-dbg/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: building package `mpd-dbg' in `../mpd-dbg_0.15.10-1ubuntu3_amd64.deb'.
dpkg-deb: warning: ignoring 1 warnings about the control file(s)
```


Do you have any solution for this ?

Thanks

---

### Post by MetalMusicAddict on 2010-11-18
Update for Maverick. (note the end)
```
DEB_CONFIGURE_USER_FLAGS += $(WITH_TREMOR) --enable-sqlite --enable-un --enable-ao **--enable-lame**
```

@ikonitas - You .conf looks fine though you might wanna enable a stereo stream.

```
format        "44100:16:**2**"
```

Make sure you use the above switch and save your changes to the rules file before you compile.

---

### Post by ikonitas on 2010-11-18
Thanks [MetalMusicAddict]("http://ohioloco.ubuntuforums.org/member.php?u=6176") for your reply : 

Its all working fine now :) 
Just one thing I would like to allow mpd to stream his output to icecast2 ... :|

---

### Post by joe_newbie on 2010-11-23
I think I have followed the instructions properly but I am still getting: output: line 221: No such encoder: lame


I am on maverick so I am using --enable-lame

Any suggestions for what I may be doing wrong?

Perhaps ikonitas could tell me what he did differently that made it work?

Joe

---

### Post by joe_newbie on 2010-11-23
A small update:

If I comment out the encoder section like so:

audio_output {
	type		"httpd"
	name		"My HTTP Stream"
#	encoder		"lame"		# optional, vorbis or lame
	port		"8000"
#	quality		"5.0"			# do not define if bitrate is defined
	bitrate		"192"			# do not define if quality is defined
	format		"44100:16:2"

Then mpd starts normally and will in fact stream on port 8000. I can listen from a web browser, but this still does not get Mpod to stream it with the onthego setting.

---

### Post by durand on 2010-11-24
This is what I've got in maverick: > DEB_CONFIGURE_USER_FLAGS += $(WITH_TREMOR) --enable-sqlite --enable-un --enable-ao --enable-lastfm --enable-lame -enable-lame-encoder
 and it seems to work great. (though I have just noticed that -enable-lame-encoder has only one -...nevertheless, it works.)

---

### Post by joe_newbie on 2010-11-25
Still no luck. When MetalMusicAddict says to pin our package in synaptic, what exactly is the procedure?

 I have been installing it with gdebi. Then when I look in synaptic it shows two versions of the package. One is described as (maverick), the other is (now). If I choose to force a particular one(now), it indicates it has a package to install. Doing the install, it still fails mentioning the lame encoder. I checked every other package that seemed related to lame is installed.

Any help is much appreciated.

Joe

---

### Post by joe_newbie on 2010-11-25
Got it working now, here is what I did:

Used synaptic to completely remove MPD and all config files.
Deleted all directories and files created during initial attempts.

Followed MetalMusicAddicts instructions again, but this time, used
--enable-lame-encoder

When using --enable-lame I noticed in the output that it said this was an invalid config.

Now I installed with gdebi, 
Edited /etc/mpd.conf to enable lame encoding from HTTPD,
sudo service mpd restart 

And voila! It works.

Sort of..

Works over local network. Seem to have trouble accessing it from the internet. Suspect router issues but shields up shows port 8000 is open.

Still working on it. Enjoying playing with this wonderful toy (linux)

Learning a lot.
Loving it.

Thanks to everyone for their help so far.


Joe

---

### Post by Brian Vaughan on 2010-11-29
I found this very helpful. Among other things, I'd been meaning to find out how to build .debs from source packages.

In using "./configure --help", I found that there was a listing for "--enable-lame-encoder", but none for "--enable-lame". At one point, I thought I had used just "--enable-lame-encoder", and it hadn't worked, so I tried both, and it seemed to work:

```
DEB_CONFIGURE_USER_FLAGS += $(WITH_TREMOR) --enable-sqlite --enable-un --enable-ao --enable-lastfm --enable-lame --enable-lame-encoder
```

One catch: the command to pull in all the build dependencies missed "libmp3lame-dev", which was required for the build.

To pin your custom build in Synaptic, find the installed package -- it will probably be listed as "Installed (Upgradeable)" under the Status tab -- right-click on it, and select "Lock this version."

---

### Post by bdrung on 2011-01-10
I stumbled over a [blog post]("http://www.produnis.de/blog/?p=1393") about enabling LAME support in mpd, which linked to this forum thread. LAME is in universe since Ubuntu 10.10 (maverick). Therefore I enabled LAME support in mpd 0.15.15-2ubuntu2, which will be in Ubuntu 11.04 (natty).

---

### Post by MetalMusicAddict on 2011-01-10
Awesome bdrung. I'm sure lots of folks will like this. :) Maybe we can get a backport for 10.10?

---

### Post by bdrung on 2011-01-10
Not backport, but Stable Release Update (SRU). I will provide the debdiff and do the upload if you open a bug report for it and subscribe me.

Here's the SRU procedure: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by MetalMusicAddict on 2011-01-10
Sure. I didn't think it would qualify for a SRU. :) And [DONE]("https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/701282").

---

### Post by bdrung on 2011-01-10
I've done my part now. This two line change is worth a SRU. It's not the first time that a SRU adds a build dependency to enable a feature.

---

### Post by MetalMusicAddict on 2011-01-14
@bdrung looks like Martin is rejecting the SRU.

This is why I suggested a backport and not a SRU. In my experience with developing Ubuntu Studio *anything* adding a new feature would fail a SRU.

I think you might have to cite the SRU where adding a build dependency enables a feature.

Should we just go for a backport? You'll need a tester or two right?

---

### Post by bdrung on 2011-01-24
The mpd upload is still in the [unapproved queue]("https://launchpad.net/ubuntu/maverick/+queue?queue_state=1&queue_text=") (not rejected yet). I gave an example where we added some build dependencies to build some modules in a SRU.

Doing a backport instead of a SRU would pull a new version of mpd instead of just enabling lame. That's why I think that a SRU is better than a backport. You can go for a backport if you want.

---

### Post by virgil_disgr4ce on 2011-02-11
Thanks for this guys—I upgraded mpd to the proposed version and mp3 streaming is working great now!  I get about 50% less latency than with the ogg encoder.  :D

---

### Post by clicker4721 on 2011-02-13
MetalMusicAddict: After I've done all that stuff you said in your first post, can I delete the half-a-million packages that were installed? I'm a bit of a space miser...

---

### Post by MetalMusicAddict on 2011-03-18
Just a note, everyone with a LP account that wants this to hit as a normal update must enable the -proposed repo and make sure it works. Then, comment [HERE]("https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/701282").

---

### Post by rage_311 on 2011-05-24
Is there any way to enable this in Lucid, by chance?

EDIT:
I've tried several times to build (on Lucid) according to MetalMusicAddict's instructions, but it always tells me that there's no such encoder as lame.  I already had mpd installed before I started trying this route... I'm wondering if there are some files left over from that install that are messing it up?  Any thoughts?

---

### Post by bonfire89 on 2011-09-01
Where does the .deb file go after running debuild? Here is what I got from debuild

```


test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "debian/build"
if test -e /usr/share/misc/config.guess ; then \
		for i in ./config.guess ; do \
			if ! test -e $i.cdbs-orig ; then \
				mv $i $i.cdbs-orig ; \
				cp --remove-destination /usr/share/misc/config.guess $i ; \
			fi ; \
		done ; \
	fi
if test -e /usr/share/misc/config.sub ; then \
		for i in ./config.sub ; do \
			if ! test -e $i.cdbs-orig ; then \
				mv $i $i.cdbs-orig ; \
				cp --remove-destination /usr/share/misc/config.sub $i ; \
			fi ; \
		done ; \
	fi
DEB_MAKE_CHECK_TARGET unset, not running checks
/usr/bin/make  -C debian/build  install DESTDIR=/mnt/sde1/music/mpd-0.15.4/debian/mpd
make[1]: Entering directory `/mnt/sde1/music/mpd-0.15.4/debian/build'
make[2]: Entering directory `/mnt/sde1/music/mpd-0.15.4/debian/build'
test -z "/usr/bin" || mkdir -p -- "/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/bin"
  /usr/bin/install -c 'src/mpd' '/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/bin/mpd'
test -z "" || mkdir -p -- "/mnt/sde1/music/mpd-0.15.4/debian/mpd"
test -z "/usr/share/doc/mpd" || mkdir -p -- "/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/doc/mpd"
 /usr/bin/install -c -m 644 '/mnt/sde1/music/mpd-0.15.4/./AUTHORS' '/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/doc/mpd/AUTHORS'
 /usr/bin/install -c -m 644 '/mnt/sde1/music/mpd-0.15.4/./COPYING' '/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/doc/mpd/COPYING'
 /usr/bin/install -c -m 644 '/mnt/sde1/music/mpd-0.15.4/./NEWS' '/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/doc/mpd/NEWS'
 /usr/bin/install -c -m 644 '/mnt/sde1/music/mpd-0.15.4/./README' '/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/doc/mpd/README'
 /usr/bin/install -c -m 644 '/mnt/sde1/music/mpd-0.15.4/./UPGRADING' '/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/doc/mpd/UPGRADING'
 /usr/bin/install -c -m 644 '/mnt/sde1/music/mpd-0.15.4/./doc/mpdconf.example' '/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/doc/mpd/mpdconf.example'
test -z "/usr/share/man/man1" || mkdir -p -- "/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/man/man1"
 /usr/bin/install -c -m 644 '/mnt/sde1/music/mpd-0.15.4/./doc/mpd.1' '/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/man/man1/mpd.1'
test -z "/usr/share/man/man5" || mkdir -p -- "/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/man/man5"
 /usr/bin/install -c -m 644 '/mnt/sde1/music/mpd-0.15.4/./doc/mpd.conf.5' '/mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/man/man5/mpd.conf.5'
test -z "" || mkdir -p -- "/mnt/sde1/music/mpd-0.15.4/debian/mpd"
test -z "" || mkdir -p -- "/mnt/sde1/music/mpd-0.15.4/debian/mpd"
make[2]: Leaving directory `/mnt/sde1/music/mpd-0.15.4/debian/build'
make[1]: Leaving directory `/mnt/sde1/music/mpd-0.15.4/debian/build'
dh_installdirs -pmpd 
dh_installdirs -pmpd-dbg 
dh_installdocs -pmpd ./README ./NEWS ./AUTHORS  
dh_installexamples -pmpd 
dh_installman -pmpd  
dh_installinfo -pmpd  
dh_installmenu -pmpd 
dh_installcron -pmpd 
dh_installinit -pmpd  -n 
Duplicate specification "O=s" for option "O"
dh_installdebconf -pmpd 
dh_installemacsen -pmpd   
dh_installcatalogs -pmpd 
dh_installpam -pmpd 
dh_installlogrotate -pmpd 
dh_installlogcheck -pmpd 
dh_installchangelogs -pmpd   
dh_installudev -pmpd 
dh_lintian -pmpd 
dh_install -pmpd  
dh_link -pmpd  
dh_installmime -pmpd 
rm -f /mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/doc/mpd/mpdconf.example
rm -f /mnt/sde1/music/mpd-0.15.4/debian/mpd/usr/share/doc/mpd/COPYING
dh_installdocs -pmpd-dbg ./README ./NEWS ./AUTHORS  
dh_installexamples -pmpd-dbg 
dh_installman -pmpd-dbg  
dh_installinfo -pmpd-dbg  
dh_installmenu -pmpd-dbg 
dh_installcron -pmpd-dbg 
dh_installinit -pmpd-dbg  -n 
Duplicate specification "O=s" for option "O"
dh_installdebconf -pmpd-dbg 
dh_installemacsen -pmpd-dbg   
dh_installcatalogs -pmpd-dbg 
dh_installpam -pmpd-dbg 
dh_installlogrotate -pmpd-dbg 
dh_installlogcheck -pmpd-dbg 
dh_installchangelogs -pmpd-dbg   
dh_installudev -pmpd-dbg 
dh_lintian -pmpd-dbg 
dh_install -pmpd-dbg  
dh_link -pmpd-dbg  
dh_installmime -pmpd-dbg 
dh_strip -pmpd  --dbg-package=mpd-dbg
dh_compress -pmpd  
dh_fixperms -pmpd -X var/* 
dh_makeshlibs -pmpd  
dh_compress -pmpd-dbg  
dh_fixperms -pmpd-dbg -X var/* 
dh_installdeb -pmpd 
dh_perl -pmpd 
dh_shlibdeps -pmpd    
dh_installdeb -pmpd-dbg 
dh_perl -pmpd-dbg 
dh_shlibdeps -pmpd-dbg    
dh_gencontrol -pmpd  
# symlink identical documentation to depending packages
[ -n "$CDBS_NO_DOC_SYMLINKING" ] || \
	[ -h debian/mpd/usr/share/doc ] || \
	[ -h debian/mpd/usr/share/doc/mpd ] || \
	[ ! -d debian/mpd/usr/share/doc ] || \
	for dep in `perl -ne 'if (/^(Pre-)?Depends:/) {s/^\w+://; foreach (split /,/) { split; print($_[0], "\n"); } }' debian/mpd/DEBIAN/control`; do \
	    if [ -d debian/$dep/usr/share/doc ]; then \
                echo "Searching for duplicated docs in dependency $dep..."; \
                rootdir=`pwd`; \
                (cd debian/mpd/usr/share/doc/mpd; find -type f ! -name copyright | while read f; do \
                    thisfile="$rootdir/debian/mpd/usr/share/doc/mpd/$f"; \
                    depfile="$rootdir/debian/$dep/usr/share/doc/$dep/$f"; \
                    if [ -f $depfile -o -L $depfile ] && zcmp $thisfile $depfile >/dev/null; then \
                        echo "  symlinking $f in mpd to file in $dep"; \
                        rm $thisfile; ln -s /usr/share/doc/$dep/$f $thisfile; \
                    fi; \
                done ); \
            fi; \
	done
# symlink identical Gnome help files within packages
if [ -z "$CDBS_NO_GNOME_HELP_SYMLINKING" ] && [ -d debian/mpd/usr/share/gnome/help ]; then \
            cd debian/mpd && LC_ALL=C fdupes -r1nq usr/share/gnome/help | while read s; do \
                set -- $(echo $s | tr ' ' '\n' | sort); \
                f=$1; shift; \
                for d; do \
                    echo "symlinking duplicate Gnome help file $d to $f"; \
                    rm $d; ln -s /$f $d; \
                done; \
            done; \
	fi
dh_link -p mpd
dh_md5sums -pmpd 
dh_builddeb -pmpd 
dpkg-deb: warning: 'debian/mpd/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: building package `mpd' in `../mpd_0.15.4-1ubuntu3_i386.deb'.
dpkg-deb: warning: ignoring 1 warnings about the control file(s)

dh_gencontrol -pmpd-dbg  
# symlink identical documentation to depending packages
[ -n "$CDBS_NO_DOC_SYMLINKING" ] || \
	[ -h debian/mpd-dbg/usr/share/doc ] || \
	[ -h debian/mpd-dbg/usr/share/doc/mpd-dbg ] || \
	[ ! -d debian/mpd-dbg/usr/share/doc ] || \
	for dep in `perl -ne 'if (/^(Pre-)?Depends:/) {s/^\w+://; foreach (split /,/) { split; print($_[0], "\n"); } }' debian/mpd-dbg/DEBIAN/control`; do \
	    if [ -d debian/$dep/usr/share/doc ]; then \
                echo "Searching for duplicated docs in dependency $dep..."; \
                rootdir=`pwd`; \
                (cd debian/mpd-dbg/usr/share/doc/mpd-dbg; find -type f ! -name copyright | while read f; do \
                    thisfile="$rootdir/debian/mpd-dbg/usr/share/doc/mpd-dbg/$f"; \
                    depfile="$rootdir/debian/$dep/usr/share/doc/$dep/$f"; \
                    if [ -f $depfile -o -L $depfile ] && zcmp $thisfile $depfile >/dev/null; then \
                        echo "  symlinking $f in mpd-dbg to file in $dep"; \
                        rm $thisfile; ln -s /usr/share/doc/$dep/$f $thisfile; \
                    fi; \
                done ); \
            fi; \
	done
Searching for duplicated docs in dependency mpd...
  symlinking ./AUTHORS in mpd-dbg to file in mpd
  symlinking ./README in mpd-dbg to file in mpd
  symlinking ./NEWS.gz in mpd-dbg to file in mpd
  symlinking ./NEWS.Debian.gz in mpd-dbg to file in mpd
  symlinking ./changelog.Debian.gz in mpd-dbg to file in mpd
# symlink identical Gnome help files within packages
if [ -z "$CDBS_NO_GNOME_HELP_SYMLINKING" ] && [ -d debian/mpd-dbg/usr/share/gnome/help ]; then \
            cd debian/mpd-dbg && LC_ALL=C fdupes -r1nq usr/share/gnome/help | while read s; do \
                set -- $(echo $s | tr ' ' '\n' | sort); \
                f=$1; shift; \
                for d; do \
                    echo "symlinking duplicate Gnome help file $d to $f"; \
                    rm $d; ln -s /$f $d; \
                done; \
            done; \
	fi
dh_link -p mpd-dbg
dh_md5sums -pmpd-dbg 
dh_builddeb -pmpd-dbg 
dpkg-deb: warning: 'debian/mpd-dbg/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: building package `mpd-dbg' in `../mpd-dbg_0.15.4-1ubuntu3_i386.deb'.
dpkg-deb: warning: ignoring 1 warnings about the control file(s)

```


UPDATE: found it "dpkg-deb: building package `mpd' in `../mpd_0.15.4-1ubuntu3_i386.deb'."

UPDATE: is this supposed to work in 10.04?

---

### Post by pataquets on 2011-12-18
MPD on Lucid fails for me.
I can stream successfully in vorbis format.
However, mpd fails to start when switching to "lame".
Seems that a Lucid backport as above would be the solution.
Those who want to show interest, mark [LP bug 906004]("https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/906004") as affecting you.

---

### Post by durand on 2011-12-18
> **pataquets said:**
> MPD on Lucid fails for me.
I can stream successfully in vorbis format.
However, mpd fails to start when switching to "lame".
Seems that a Lucid backport as above would be the solution.
Those who want to show interest, mark [LP bug 906004]("https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/906004") as affecting you.

It is probably quicker to just compile it yourself rather than wait for a backport which will probably never come.

---

### Post by inobe on 2011-12-18
what ever happened to Sockso media server [http://sockso.pu-gh.com/](http://sockso.pu-gh.com/)

simple web face any browser could load, works over a lan or the entire web:p

---

### Post by durand on 2011-12-18
It needs a web browser whereas this solution works without one. There's also ampache or google music if you want something like sockso.

---

### Post by inobe on 2011-12-18
> **durand said:**
> It needs a web browser


i think you can stream to your own player too, winamp, wmp, itunes...

---

### Post by durand on 2011-12-18
Ah ok but the other difference is that using MPD makes streaming more radio like. There is only one song being played to everyone listening to the stream with mpd whereas with sockso, each listener chooses their own song. Both programs are used for different reasons :)

---

### Post by inobe on 2011-12-18
i see, that radio stuff sounds good.

seen a stupid iphone app for it somewhere, i can't find the real app :lol:

---

