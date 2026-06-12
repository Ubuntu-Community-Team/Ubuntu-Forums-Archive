---
title: "Ubuntu 12.10 (minimum install) to record sound"
date: 2012-10-28
forum: Multimedia Software
---

### Post by Minimos on 2012-10-28
I have a small computer, a Fit pc2i, based on a Atom Z530 platform, which I would like to use to record and playback audio. The specifications of the device can be found here:

[http://www.fit-pc.com/web/fit-pc/fit-pc2i-specifications/](http://www.fit-pc.com/web/fit-pc/fit-pc2i-specifications/)

I've seen that starting from Ubuntu 12.10, the audio codec "opus" is supported by default, so I would like to install Ubuntu 12.10 on that device. Without GUI at the moment, after the installation of Ubuntu I take control with ssh.

For the installation of Ubuntu 12.10, I used the "mini.iso" (the webinstall ISO for Ubuntu 12.10 i386), so I can be sure that no packages are installed that I don't need; since I want the pc to be fast. During the "web installation" of Ubuntu, I didn't select any packages to install, except for "OpenSSH server".

Once the Ubuntu installation was complete, I installed opus, I installed ffmpeg, I installed ALSA (and later I also installed pulseaudio).

When I plug in the micro in the one jack, and the headphone in the other jack, and when I do the command "arecord | aplay", I should be able to hear myself, but I don't.

The strange thing is, when I boot that PC with a Live-CD of Ubuntu 12.10 Desktop (full CD that is), and I go to the command line, when I do the command "arecord | aplay", I do hear myself; the result I want and I would expect.

So my guesses are that in my "light" install of ubuntu, I am missing some settings or some packages which allow me to record audio.

I've already looked up on the internet what the problem could be, I tried various things (see attachments), but I can't seem to find the problem.

Could someone shed some light on my problem?

**_This is the situation where everything works (live-cd):_**

Alsamixer part 1
[IMG]http://oi49.tinypic.com/qzmy45.jpg[/IMG]

Alsamixer part 2
[IMG]http://oi49.tinypic.com/w7czmv.jpg[/IMG]

Alsamixer part 3
[IMG]http://oi45.tinypic.com/35jjw9c.jpg[/IMG]

Some commands:
```

**root@host:~# [COLOR="Red"]ls -hl /dev/snd[/COLOR]**
total 0
drwxr-xr-x  2 root root       60 Oct 28 11:01 by-path
crw-rw---T+ 1 root audio 116,  7 Oct 28 11:01 controlC0
crw-rw---T+ 1 root audio 116,  6 Oct 28 11:01 hwC0D0
crw-rw---T+ 1 root audio 116,  5 Oct 28 11:52 pcmC0D0c
crw-rw---T+ 1 root audio 116,  4 Oct 28 11:52 pcmC0D0p
crw-rw---T+ 1 root audio 116,  3 Oct 28 11:01 pcmC0D1p
crw-rw---T+ 1 root audio 116,  2 Oct 28 11:01 pcmC0D2c
crw-rw---T+ 1 root audio 116,  1 Oct 28 11:01 seq
crw-rw---T+ 1 root audio 116, 33 Oct 28 11:01 timer

**root@host:~# [COLOR="red"]arecord -l[/COLOR]**
**** List of CAPTURE Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 2: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
  
**root@host:~# [COLOR="red"]arecord -L[/COLOR]**
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=MID
    HDA Intel MID, ALC662 rev1 Analog
    Default Audio Device
front:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    Front speakers
surround40:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    Direct sample mixing device
dmix:CARD=MID,DEV=2
    HDA Intel MID, ALC662 rev1 Analog
    Direct sample mixing device
dsnoop:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    Direct sample snooping device
dsnoop:CARD=MID,DEV=2
    HDA Intel MID, ALC662 rev1 Analog
    Direct sample snooping device
hw:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    Direct hardware device without any conversions
hw:CARD=MID,DEV=2
    HDA Intel MID, ALC662 rev1 Analog
    Direct hardware device without any conversions
plughw:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    Hardware device with all software conversions
plughw:CARD=MID,DEV=2
    HDA Intel MID, ALC662 rev1 Analog
    Hardware device with all software conversions
	
**root@host:~# [COLOR="red"]lsmod[/COLOR]**
Module                  Size  Used by
dm_crypt               22402  0 
arc4                   12473  2 
snd_hda_codec_realtek    63356  1 
gpio_sch               12928  0 
i2c_isch               12639  0 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
rt2800usb              22285  0 
snd_hwdep              13272  1 snd_hda_codec
rt2800lib              57144  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              19941  1 rt2800usb
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
coretemp               13168  0 
rt2x00lib              48562  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              461161  3 rt2800lib,rt2x00usb,rt2x00lib
snd_seq_midi           13132  0 
dm_multipath           22365  0 
kvm                   357806  0 
scsi_dh                14178  1 dm_multipath
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
microcode              18209  0 
cfg80211              175375  2 rt2x00lib,mac80211
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
psmouse                84843  0 
snd_timer              24411  2 snd_pcm,snd_seq
serio_raw              13031  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_sch                12727  0 
snd                    61991  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13037  0 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
parport_pc             31968  0 
bnep                   17707  2 
ppdev                  12817  0 
rfcomm                 37276  0 
lp                     13299  0 
bluetooth             183228  10 bnep,rfcomm
parport                40753  3 parport_pc,ppdev,lp
squashfs               35834  1 
overlayfs              27233  1 
nls_iso8859_1          12617  1 
dm_raid45              75357  0 
xor                    26090  1 dm_raid45
dm_mirror              21665  0 
dm_region_hash         15977  1 dm_mirror
dm_log                 18137  3 dm_raid45,dm_mirror,dm_region_hash
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
gma500_gfx            187730  2 
pata_sch               12700  1 
drm_kms_helper         45271  1 gma500_gfx
r8169                  55976  0 
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
drm                   230463  3 gma500_gfx,drm_kms_helper
i2c_algo_bit           13197  1 gma500_gfx
video                  18847  1 gma500_gfx
usb_storage            39350  1 

```

Installed packages:
```

**root@host:~# [COLOR="Red"]dpkg --get-selections[/COLOR]**
account-plugin-aim				install
account-plugin-facebook				install
account-plugin-flickr				install
account-plugin-google				install
account-plugin-icons				install
account-plugin-identica				install
account-plugin-jabber				install
account-plugin-salut				install
account-plugin-twitter				install
account-plugin-windows-live			install
account-plugin-yahoo				install
accountsservice					install
acl						install
acpi-support					install
acpid						install
activity-log-manager-common			install
activity-log-manager-control-center		install
adduser						install
adium-theme-ubuntu				install
aisleriot					install
alsa-base					install
alsa-utils					install
anacron						install
apg						install
app-install-data				install
app-install-data-partner			install
apparmor					install
appmenu-gtk					install
appmenu-gtk3					install
appmenu-qt					install
apport						install
apport-gtk					install
apport-symptoms					install
apt						install
apt-clone					install
apt-transport-https				install
apt-utils					install
apt-xapian-index				install
aptdaemon					install
aptdaemon-data					install
apturl						install
apturl-common					install
archdetect-deb					install
aspell						install
aspell-en					install
at						install
at-spi2-core					install
avahi-autoipd					install
avahi-daemon					install
avahi-utils					install
bamfdaemon					install
baobab						install
base-files					install
base-passwd					install
bash						install
bash-completion					install
bc						install
bind9-host					install
binutils					install
bluez						install
bluez-alsa:i386					install
bluez-cups					install
bluez-gstreamer					install
branding-ubuntu					install
brasero						install
brasero-cdrkit					install
brasero-common					install
brltty						install
bsdmainutils					install
bsdutils					install
btrfs-tools					install
busybox-initramfs				install
busybox-static					install
bzip2						install
ca-certificates					install
casper						install
checkbox					install
checkbox-qt					install
cifs-utils					install
colord						install
command-not-found				install
command-not-found-data				install
compiz						install
compiz-core					install
compiz-gnome					install
compiz-plugins-default				install
console-setup					install
consolekit					install
coreutils					install
cpio						install
cpp						install
cpp-4.7						install
cracklib-runtime				install
crda						install
cron						install
cryptsetup					install
cryptsetup-bin					install
cups						install
cups-bsd					install
cups-client					install
cups-common					install
cups-filters					install
cups-ppdc					install
dash						install
dbus						install
dbus-x11					install
dc						install
dconf-gsettings-backend:i386			install
dconf-service					install
dconf-tools					install
debconf						install
debconf-i18n					install
debianutils					install
deja-dup					install
desktop-file-utils				install
dictionaries-common				install
diffstat					install
diffutils					install
dmidecode					install
dmraid						install
dmsetup						install
dmz-cursor-theme				install
dnsmasq-base					install
dnsutils					install
doc-base					install
dosfstools					install
dpkg						install
dpkg-repack					install
duplicity					install
dvd+rw-tools					install
e2fslibs:i386					install
e2fsprogs					install
ecryptfs-utils					install
ed						install
eject						install
empathy						install
empathy-common					install
enchant						install
eog						install
espeak-data:i386				install
evince						install
evince-common					install
evolution-data-server				install
evolution-data-server-common			install
example-content					install
file						install
file-roller					install
findutils					install
firefox						install
firefox-globalmenu				install
firefox-gnome-support				install
firefox-locale-de				install
firefox-locale-en				install
firefox-locale-es				install
firefox-locale-pt				install
firefox-locale-zh-hans				install
folks-common					install
fontconfig					install
fontconfig-config				install
fonts-freefont-ttf				install
fonts-kacst					install
fonts-kacst-one					install
fonts-khmeros-core				install
fonts-lao					install
fonts-liberation				install
fonts-lklug-sinhala				install
fonts-nanum					install
fonts-opensymbol				install
fonts-sil-abyssinica				install
fonts-sil-padauk				install
fonts-takao-pgothic				install
fonts-thai-tlwg					install
fonts-tibetan-machine				install
fonts-tlwg-garuda				install
fonts-tlwg-kinnari				install
fonts-tlwg-loma					install
fonts-tlwg-mono					install
fonts-tlwg-norasi				install
fonts-tlwg-purisa				install
fonts-tlwg-sawasdee				install
fonts-tlwg-typewriter				install
fonts-tlwg-typist				install
fonts-tlwg-typo					install
fonts-tlwg-umpush				install
fonts-tlwg-waree				install
foomatic-db-compressed-ppds			install
foomatic-db-engine				install
foomatic-filters				install
freerdp-x11					install
friendly-recovery				install
ftp						install
fuse						install
gcalctool					install
gcc						install
gcc-4.7						install
gcc-4.7-base:i386				install
gconf-service					install
gconf-service-backend				install
gconf2						install
gconf2-common					install
gcr						install
gdb						install
gedit						install
gedit-common					install
genisoimage					install
geoclue						install
geoclue-ubuntu-geoip				install
geoip-database					install
gettext						install
gettext-base					install
ghostscript					install
ghostscript-cups				install
ghostscript-x					install
gir1.2-accounts-1.0				install
gir1.2-appindicator3-0.1			install
gir1.2-atk-1.0					install
gir1.2-atspi-2.0				install
gir1.2-dbusmenu-glib-0.4			install
gir1.2-dee-1.0					install
gir1.2-freedesktop				install
gir1.2-gdata-0.0				install
gir1.2-gdkpixbuf-2.0				install
gir1.2-glib-2.0					install
gir1.2-gmenu-3.0				install
gir1.2-gnomebluetooth-1.0			install
gir1.2-gnomekeyring-1.0				install
gir1.2-goa-1.0					install
gir1.2-gst-plugins-base-0.10			install
gir1.2-gstreamer-0.10				install
gir1.2-gtk-3.0					install
gir1.2-gtksource-3.0				install
gir1.2-gudev-1.0				install
gir1.2-indicate-0.7				install
gir1.2-javascriptcoregtk-3.0			install
gir1.2-json-1.0					install
gir1.2-messagingmenu-1.0			install
gir1.2-notify-0.7				install
gir1.2-pango-1.0				install
gir1.2-peas-1.0					install
gir1.2-rb-3.0					install
gir1.2-signon-1.0				install
gir1.2-soup-2.4					install
gir1.2-syncmenu-0.1				install
gir1.2-timezonemap-1.0				install
gir1.2-totem-1.0				install
gir1.2-totem-plparser-1.0			install
gir1.2-ubuntuoneui-3.0				install
gir1.2-unity-5.0:i386				install
gir1.2-vte-2.90					install
gir1.2-webkit-3.0				install
gir1.2-wnck-3.0					install
gir1.2-xkl-1.0					install
gksu						install
glib-networking:i386				install
glib-networking-common				install
glib-networking-services			install
gnome-accessibility-themes			install
gnome-bluetooth					install
gnome-contacts					install
gnome-control-center				install
gnome-control-center-data			install
gnome-control-center-signon			install
gnome-desktop3-data				install
gnome-disk-utility				install
gnome-font-viewer				install
gnome-games-data				install
gnome-icon-theme				install
gnome-icon-theme-symbolic			install
gnome-keyring					install
gnome-mahjongg					install
gnome-media					install
gnome-menus					install
gnome-online-accounts				install
gnome-orca					install
gnome-power-manager				install
gnome-screensaver				install
gnome-screenshot				install
gnome-session					install
gnome-session-bin				install
gnome-session-canberra				install
gnome-session-common				install
gnome-settings-daemon				install
gnome-sudoku					install
gnome-system-log				install
gnome-system-monitor				install
gnome-terminal					install
gnome-terminal-data				install
gnome-user-guide				install
gnome-user-share				install
gnomine						install
gnupg						install
gparted						install
gpgv						install
grep						install
groff-base					install
growisofs					install
grub-common					install
grub-gfxpayload-lists				install
grub-pc						install
grub-pc-bin					install
grub2-common					install
gsettings-desktop-schemas			install
gsfonts						install
gstreamer0.10-alsa:i386				install
gstreamer0.10-gconf:i386			install
gstreamer0.10-nice:i386				install
gstreamer0.10-plugins-base:i386			install
gstreamer0.10-plugins-base-apps			install
gstreamer0.10-plugins-good:i386			install
gstreamer0.10-pulseaudio:i386			install
gstreamer0.10-tools				install
gstreamer0.10-x:i386				install
gtk2-engines:i386				install
gtk2-engines-murrine:i386			install
gtk3-engines-unico				install
gucharmap					install
guile-1.8-libs					install
gvfs:i386					install
gvfs-backends					install
gvfs-bin					install
gvfs-common					install
gvfs-daemons					install
gvfs-fuse					install
gvfs-libs:i386					install
gwibber						install
gwibber-service					install
gwibber-service-facebook			install
gwibber-service-identica			install
gwibber-service-twitter				install
gzip						install
hardening-includes				install
hdparm						install
hicolor-icon-theme				install
hostname					install
hpijs						install
hplip						install
hplip-data					install
humanity-icon-theme				install
hunspell-en-us					install
hwdata						install
ibus						install
ibus-gtk:i386					install
ibus-gtk3:i386					install
ibus-pinyin					install
ibus-pinyin-db-android				install
ibus-table					install
ifupdown					install
im-switch					install
indicator-application				install
indicator-appmenu				install
indicator-datetime				install
indicator-messages				install
indicator-power					install
indicator-printers				install
indicator-session				install
indicator-sound					install
info						install
initramfs-tools					install
initramfs-tools-bin				install
initscripts					install
inputattach					install
insserv						install
install-info					install
intel-gpu-tools					install
intltool-debian					install
iproute						install
iptables					install
iputils-arping					install
iputils-ping					install
iputils-tracepath				install
irqbalance					install
isc-dhcp-client					install
isc-dhcp-common					install
iso-codes					install
iw						install
jfsutils					install
kbd						install
kerneloops-daemon				install
keyboard-configuration				install
keyutils					install
klibc-utils					install
kpartx						install
kpartx-boot					install
krb5-locales					install
landscape-client-ui-install			install
language-pack-de				install
language-pack-de-base				install
language-pack-en				install
language-pack-en-base				install
language-pack-es				install
language-pack-es-base				install
language-pack-gnome-de				install
language-pack-gnome-de-base			install
language-pack-gnome-en				install
language-pack-gnome-en-base			install
language-pack-gnome-es				install
language-pack-gnome-es-base			install
language-pack-gnome-pt				install
language-pack-gnome-pt-base			install
language-pack-gnome-zh-hans			install
language-pack-gnome-zh-hans-base		install
language-pack-pt				install
language-pack-pt-base				install
language-pack-zh-hans				install
language-pack-zh-hans-base			install
language-selector-common			install
language-selector-gnome				install
laptop-detect					install
less						install
libaa1:i386					install
libaccount-plugin-1.0-0				install
libaccounts-glib0				install
libaccounts-qt1					install
libaccountsservice0				install
libacl1:i386					install
libappindicator1				install
libappindicator3-1				install
libapt-inst1.5:i386				install
libapt-pkg-perl					install
libapt-pkg4.12:i386				install
libarchive-zip-perl				install
libarchive12:i386				install
libart-2.0-2:i386				install
libasn1-8-heimdal:i386				install
libasound2:i386					install
libasound2-plugins:i386				install
libaspell15					install
libasprintf0c2:i386				install
libasyncns0:i386				install
libatasmart4:i386				install
libatk-adaptor:i386				install
libatk-adaptor-data				install
libatk-bridge2.0-0:i386				install
libatk1.0-0:i386				install
libatk1.0-data					install
libatkmm-1.6-1:i386				install
libatspi2.0-0:i386				install
libattr1:i386					install
libaudio2:i386					install
libavahi-client3:i386				install
libavahi-common-data:i386			install
libavahi-common3:i386				install
libavahi-core7:i386				install
libavahi-glib1:i386				install
libavahi-gobject0:i386				install
libavc1394-0:i386				install
libbamf3-0:i386					install
libbind9-80					install
libblkid1:i386					install
libbluetooth3:i386				install
libboost-date-time1.49.0			install
libbrasero-media3-1				install
libbrlapi0.5:i386				install
libbsd0:i386					install
libburn4					install
libbz2-1.0:i386					install
libc-bin					install
libc-dev-bin					install
libc6:i386					install
libc6-dev:i386					install
libcaca0:i386					install
libcairo-gobject2:i386				install
libcairo-perl					install
libcairo2:i386					install
libcairomm-1.0-1:i386				install
libcamel-1.2-40					install
libcanberra-gtk-module:i386			install
libcanberra-gtk0:i386				install
libcanberra-gtk3-0:i386				install
libcanberra-gtk3-module:i386			install
libcanberra-pulse:i386				install
libcanberra0:i386				install
libcap-ng0					install
libcap2:i386					install
libcap2-bin					install
libcdio-cdda1					install
libcdio-paranoia1				install
libcdio13					install
libcdparanoia0:i386				install
libck-connector0:i386				install
libclass-accessor-perl				install
libclass-isa-perl				install
libclone-perl					install
libclutter-1.0-0:i386				install
libclutter-1.0-common				install
libclutter-gst-1.0-0:i386			install
libclutter-gtk-1.0-0:i386			install
libcmis-0.2-2					install
libcogl-common					install
libcogl-pango0:i386				install
libcogl9:i386					install
libcolord1:i386					install
libcomerr2:i386					install
libcompizconfig0				install
libcrack2					install
libcroco3:i386					install
libcrypt-passwdmd5-perl				install
libcryptsetup4					install
libcups2:i386					install
libcupscgi1:i386				install
libcupsfilters1:i386				install
libcupsimage2:i386				install
libcupsmime1:i386				install
libcupsppdc1:i386				install
libcurl3:i386					install
libcurl3-gnutls:i386				install
libcurl3-nss:i386				install
libdaemon0					install
libdatrie1:i386					install
libdb5.1:i386					install
libdbus-1-3:i386				install
libdbus-glib-1-2:i386				install
libdbusmenu-glib4:i386				install
libdbusmenu-gtk3-4:i386				install
libdbusmenu-gtk4:i386				install
libdbusmenu-qt2:i386				install
libdconf1:i386					install
libdebconfclient0				install
libdebian-installer4				install
libdecoration0					install
libdee-1.0-4					install
libdevmapper-event1.02.1:i386			install
libdevmapper1.02.1:i386				install
libdigest-hmac-perl				install
libdiscid0:i386					install
libdjvulibre-text				install
libdjvulibre21					install
libdmapsharing-3.0-2				install
libdmraid1.0.0.rc16				install
libdns81					install
libdotconf1.0					install
libdpkg-perl					install
libdrm-intel1:i386				install
libdrm-nouveau1a:i386				install
libdrm-nouveau2:i386				install
libdrm-radeon1:i386				install
libdrm2:i386					install
libdv4:i386					install
libebackend-1.2-5				install
libebook-1.2-14					install
libecal-1.2-15					install
libecryptfs0					install
libedata-book-1.2-15				install
libedata-cal-1.2-18				install
libedataserver-1.2-17				install
libedit2:i386					install
libelf1:i386					install
libemail-valid-perl				install
libenchant1c2a					install
libespeak1:i386					install
libevdocument3-4				install
libevent-2.0-5:i386				install
libevview3-3					install
libexempi3:i386					install
libexif12:i386					install
libexiv2-12					install
libexpat1:i386					install
libexttextcat-1.0-0				install
libexttextcat-data				install
libfarstream-0.1-0:i386				install
libffi6:i386					install
libfile-basedir-perl				install
libfile-copy-recursive-perl			install
libfile-desktopentry-perl			install
libfile-fcntllock-perl				install
libfile-mimeinfo-perl				install
libflac8:i386					install
libfolks-eds25					install
libfolks-telepathy25				install
libfolks25					install
libfontconfig1:i386				install
libfontembed1:i386				install
libfontenc1:i386				install
libframe6:i386					install
libfreerdp-plugins-standard			install
libfreerdp1					install
libfreetype6:i386				install
libfribidi0:i386				install
libfs6:i386					install
libfuse2:i386					install
libgail-3-0:i386				install
libgail-common:i386				install
libgail18:i386					install
libgcc1:i386					install
libgck-1-0					install
libgconf-2-4:i386				install
libgcr-3-1					install
libgcr-3-common					install
libgcrypt11:i386				install
libgd2-xpm:i386					install
libgdata-common					install
libgdata13					install
libgdbm3:i386					install
libgdk-pixbuf2.0-0:i386				install
libgdk-pixbuf2.0-common				install
libgee2:i386					install
libgeis1:i386					install
libgeoclue0					install
libgeoip1:i386					install
libgettextpo0:i386				install
libgexiv2-1					install
libgirepository-1.0-1				install
libgksu2-0					install
libgl1-mesa-dri:i386				install
libgl1-mesa-glx:i386				install
libglapi-mesa:i386				install
libglew1.8:i386					install
libglewmx1.8:i386				install
libglib-perl					install
libglib2.0-0:i386				install
libglib2.0-bin					install
libglib2.0-data					install
libglibmm-2.4-1c2a:i386				install
libglu1-mesa:i386				install
libgmime-2.6-0					install
libgmp10:i386					install
libgnome-bluetooth11				install
libgnome-control-center1			install
libgnome-desktop-3-4				install
libgnome-keyring-common				install
libgnome-keyring0:i386				install
libgnome-media-profiles-3.0-0			install
libgnome-menu-3-0				install
libgnome-menu2					install
libgnomekbd-common				install
libgnomekbd8					install
libgnutls26:i386				install
libgoa-1.0-0:i386				install
libgoa-1.0-common				install
libgomp1:i386					install
libgpg-error0:i386				install
libgpgme11					install
libgphoto2-2:i386				install
libgphoto2-l10n					install
libgphoto2-port0:i386				install
libgpm2:i386					install
libgpod-common					install
libgpod4:i386					install
libgrail5					install
libgrip0					install
libgs9						install
libgs9-common					install
libgssapi-krb5-2:i386				install
libgssapi3-heimdal:i386				install
libgssdp-1.0-3					install
libgstreamer-plugins-base0.10-0:i386		install
libgstreamer0.10-0:i386				install
libgtk-3-0:i386					install
libgtk-3-bin					install
libgtk-3-common					install
libgtk2-perl					install
libgtk2.0-0:i386				install
libgtk2.0-bin					install
libgtk2.0-common				install
libgtkmm-2.4-1c2a:i386				install
libgtkmm-3.0-1:i386				install
libgtksourceview-3.0-0:i386			install
libgtksourceview-3.0-common			install
libgtkspell-3-0					install
libgtop2-7					install
libgtop2-common					install
libgucharmap-2-90-7				install
libgudev-1.0-0:i386				install
libgupnp-1.0-4					install
libgupnp-igd-1.0-4:i386				install
libgusb2					install
libgutenprint2					install
libgweather-3-1					install
libgweather-common				install
libgwibber-gtk3					install
libgwibber3					install
libgxps2:i386					install
libhcrypto4-heimdal:i386			install
libheimbase1-heimdal:i386			install
libheimntlm0-heimdal:i386			install
libhpmud0					install
libhunspell-1.3-0:i386				install
libhx509-5-heimdal:i386				install
libhyphen0					install
libibus-1.0-0:i386				install
libical0					install
libice6:i386					install
libicu48:i386					install
libidn11:i386					install
libido3-0.1-0:i386				install
libiec61883-0:i386				install
libieee1284-3:i386				install
libijs-0.35					install
libimobiledevice3				install
libindicate5					install
libindicator3-7					install
libindicator7					install
libio-pty-perl					install
libio-socket-inet6-perl				install
libio-string-perl				install
libipc-run-perl					install
libisc83					install
libisccc80					install
libisccfg82					install
libisofs6					install
libitm1:i386					install
libiw30:i386					install
libjack-jackd2-0:i386				install
libjasper1:i386					install
libjavascriptcoregtk-3.0-0			install
libjbig0:i386					install
libjbig2dec0					install
libjpeg-turbo8:i386				install
libjpeg8:i386					install
libjs-jquery					install
libjson-glib-1.0-0:i386				install
libjson0:i386					install
libjte1						install
libk5crypto3:i386				install
libkeyutils1:i386				install
libklibc					install
libkms1:i386					install
libkpathsea6					install
libkrb5-26-heimdal:i386				install
libkrb5-3:i386					install
libkrb5support0:i386				install
liblcms1:i386					install
liblcms2-2:i386					install
libldap-2.4-2:i386				install
liblightdm-gobject-1-0				install
liblircclient0					install
libllvm3.1:i386					install
liblocale-gettext-perl				install
liblockfile-bin					install
liblockfile1:i386				install
liblouis-data					install
liblouis2:i386					install
libltdl7:i386					install
liblua5.1-0:i386				install
liblvm2app2.2:i386				install
liblwres80					install
liblzma5:i386					install
libmagic1:i386					install
libmailtools-perl				install
libmeanwhile1					install
libmessaging-menu0				install
libmetacity-private0a				install
libmhash2					install
libminiupnpc8					install
libmission-control-plugins0			install
libmng1:i386					install
libmount1:i386					install
libmpc2:i386					install
libmpfr4:i386					install
libmtdev1:i386					install
libmtp-common					install
libmtp-runtime					install
libmtp9:i386					install
libmusicbrainz5-0:i386				install
libmx-1.0-2:i386				install
libmx-bin					install
libmx-common					install
libmythes-1.2-0					install
libnatpmp1					install
libnautilus-extension1a				install
libncurses5:i386				install
libncursesw5:i386				install
libneon27-gnutls				install
libnet-dns-perl					install
libnet-domain-tld-perl				install
libnet-ip-perl					install
libnetfilter-conntrack3:i386			install
libnettle4:i386					install
libnewt0.52					install
libnfnetlink0					install
libnice10:i386					install
libnih-dbus1:i386				install
libnih1:i386					install
libnl-3-200:i386				install
libnl-genl-3-200:i386				install
libnl-route-3-200:i386				install
libnm-glib-vpn1					install
libnm-glib4					install
libnm-gtk-common				install
libnm-gtk0					install
libnm-util2					install
libnotify-bin					install
libnotify4:i386					install
libnspr4:i386					install
libnss-mdns					install
libnss3:i386					install
libnss3-1d:i386					install
libnuma1					install
libnux-3.0-0					install
libnux-3.0-common				install
liboauth0:i386					install
libogg0:i386					install
libopencc1:i386					install
libopenobex1					install
liborc-0.4-0:i386				install
libp11-kit0:i386				install
libpackagekit-glib2-14:i386			install
libpam-cap:i386					install
libpam-ck-connector:i386			install
libpam-freerdp					install
libpam-gnome-keyring				install
libpam-modules:i386				install
libpam-modules-bin				install
libpam-runtime					install
libpam-xdg-support:i386				install
libpam0g:i386					install
libpango-perl					install
libpango1.0-0:i386				install
libpangomm-1.4-1:i386				install
libpaper-utils					install
libpaper1:i386					install
libparse-debianchangelog-perl			install
libparted0debian1:i386				install
libpcap0.8:i386					install
libpci3:i386					install
libpciaccess0:i386				install
libpcre3:i386					install
libpcsclite1:i386				install
libpeas-1.0-0					install
libpeas-common					install
libperl5.14					install
libpipeline1:i386				install
libpixman-1-0:i386				install
libplist1					install
libplymouth2					install
libpng12-0:i386					install
libpolkit-agent-1-0:i386			install
libpolkit-backend-1-0:i386			install
libpolkit-gobject-1-0:i386			install
libpoppler-glib8:i386				install
libpoppler28:i386				install
libpopt0:i386					install
libportaudio2:i386				install
libprocps0:i386					install
libprotobuf7					install
libprotoc7					install
libproxy1:i386					install
libproxy1-plugin-gsettings:i386			install
libproxy1-plugin-networkmanager:i386		install
libpth20					install
libpulse-mainloop-glib0:i386			install
libpulse0:i386					install
libpulsedsp:i386				install
libpurple-bin					install
libpurple0					install
libpwquality1					install
libpython2.7					install
libpython3.2					install
libqjson0:i386					install
libqpdf8:i386					install
libqt4-dbus:i386				install
libqt4-declarative:i386				install
libqt4-designer:i386				install
libqt4-help:i386				install
libqt4-network:i386				install
libqt4-script:i386				install
libqt4-scripttools:i386				install
libqt4-sql:i386					install
libqt4-sql-sqlite:i386				install
libqt4-svg:i386					install
libqt4-test:i386				install
libqt4-xml:i386					install
libqt4-xmlpatterns:i386				install
libqtassistantclient4:i386			install
libqtcore4:i386					install
libqtgui4:i386					install
libqtwebkit4:i386				install
libquadmath0:i386				install
libquvi-scripts					install
libquvi7:i386					install
libraptor2-0					install
librasqal3					install
libraw1394-11:i386				install
libraw5:i386					install
librdf0						install
libreadline5:i386				install
libreadline6:i386				install
libreoffice-base-core				install
libreoffice-calc				install
libreoffice-common				install
libreoffice-core				install
libreoffice-draw				install
libreoffice-emailmerge				install
libreoffice-gnome				install
libreoffice-gtk					install
libreoffice-help-en-us				install
libreoffice-impress				install
libreoffice-math				install
libreoffice-ogltrans				install
libreoffice-pdfimport				install
libreoffice-presentation-minimizer		install
libreoffice-presenter-console			install
libreoffice-style-human				install
libreoffice-style-tango				install
libreoffice-writer				install
librest-0.7-0:i386				install
librhythmbox-core6				install
libroken18-heimdal:i386				install
librsvg2-2:i386					install
librsvg2-common:i386				install
librsync1:i386					install
librtmp0:i386					install
libsamplerate0:i386				install
libsane:i386					install
libsane-common					install
libsane-hpaio					install
libsasl2-2:i386					install
libsasl2-modules:i386				install
libsecret-1-0					install
libsecret-common				install
libselinux1:i386				install
libsensors4:i386				install
libsgutils2-2					install
libshout3:i386					install
libsigc++-2.0-0c2a:i386				install
libsignon-extension1				install
libsignon-glib1					install
libsignon-plugins-common1			install
libsignon-qt1					install
libslang2:i386					install
libsm6:i386					install
libsmbclient:i386				install
libsndfile1:i386				install
libsnmp-base					install
libsnmp15					install
libsocket6-perl					install
libsonic0:i386					install
libsoup-gnome2.4-1:i386				install
libsoup2.4-1:i386				install
libspectre1:i386				install
libspeechd2:i386				install
libspeex1:i386					install
libspeexdsp1:i386				install
libsqlite3-0:i386				install
libss2:i386					install
libssh-4:i386					install
libssl1.0.0:i386				install
libstartup-notification0:i386			install
libstdc++6:i386					install
libstlport4.6ldbl				install
libsub-name-perl				install
libswitch-perl					install
libsync-menu1:i386				install
libsyncdaemon-1.0-1				install
libsysfs2:i386					install
libt1-5						install
libtag1-vanilla:i386				install
libtag1c2a:i386					install
libtalloc2:i386					install
libtasn1-3:i386					install
libtdb1:i386					install
libtelepathy-farstream2:i386			install
libtelepathy-glib0:i386				install
libtelepathy-logger2:i386			install
libtext-charwidth-perl				install
libtext-iconv-perl				install
libtext-wrapi18n-perl				install
libthai-data					install
libthai0:i386					install
libtheora0:i386					install
libtiff5:i386					install
libtimedate-perl				install
libtimezonemap1					install
libtinfo5:i386					install
libtotem-plparser17				install
libtotem0					install
libtxc-dxtn-s2tc0:i386				install
libubuntuoneui-3.0-1				install
libudev0:i386					install
libudisks2-0:i386				install
libufe-xidgetter0				install
libunistring0:i386				install
libunity-core-6.0-5				install
libunity-misc4					install
libunity-protocol-private0:i386			install
libunity-webapps0				install
libunity9:i386					install
libupower-glib1					install
liburi-perl					install
libusb-0.1-4:i386				install
libusb-1.0-0:i386				install
libusbmuxd2					install
libutempter0					install
libuuid-perl					install
libuuid1:i386					install
libv4l-0:i386					install
libv4lconvert0:i386				install
libvisual-0.4-0:i386				install
libvisual-0.4-plugins:i386			install
libvncserver0:i386				install
libvorbis0a:i386				install
libvorbisenc2:i386				install
libvorbisfile3:i386				install
libvte-2.90-9					install
libvte-2.90-common				install
libwacom-common					install
libwacom2:i386					install
libwavpack1:i386				install
libwbclient0:i386				install
libwebkitgtk-3.0-0				install
libwebkitgtk-3.0-common				install
libwhoopsie0					install
libwind0-heimdal:i386				install
libwmf0.2-7					install
libwmf0.2-7-gtk					install
libwnck-3-0					install
libwnck-3-common				install
libwnck-common					install
libwnck22					install
libwpd-0.9-9					install
libwpg-0.2-2					install
libwps-0.2-2					install
libwrap0:i386					install
libx11-6:i386					install
libx11-data					install
libx11-xcb1:i386				install
libx86-1:i386					install
libxapian22					install
libxatracker1:i386				install
libxau6:i386					install
libxaw7:i386					install
libxcb-dri2-0:i386				install
libxcb-glx0:i386				install
libxcb-render0:i386				install
libxcb-shape0:i386				install
libxcb-shm0:i386				install
libxcb-util0:i386				install
libxcb1:i386					install
libxcomposite1:i386				install
libxcursor1:i386				install
libxdamage1:i386				install
libxdmcp6:i386					install
libxext6:i386					install
libxfixes3:i386					install
libxfont1					install
libxft2:i386					install
libxi6:i386					install
libxinerama1:i386				install
libxkbfile1:i386				install
libxklavier16					install
libxml2:i386					install
libxmu6:i386					install
libxmuu1:i386					install
libxp6:i386					install
libxpm4:i386					install
libxrandr2:i386					install
libxrender1:i386				install
libxres1:i386					install
libxslt1.1:i386					install
libxt6:i386					install
libxtst6:i386					install
libxv1:i386					install
libxvmc1					install
libxxf86dga1:i386				install
libxxf86vm1:i386				install
libyajl2					install
libyaml-tiny-perl				install
libyelp0					install
libzeitgeist-1.0-1				install
libzephyr4					install
light-themes					install
lightdm						install
lightdm-remote-session-freerdp			install
lightdm-remote-session-uccsconfigure		install
lintian						install
linux-firmware					install
linux-generic					install
linux-headers-3.5.0-17				install
linux-headers-3.5.0-17-generic			install
linux-headers-generic				install
linux-headers-generic-pae			install
linux-image-3.5.0-17-generic			install
linux-image-extra-3.5.0-17-generic		install
linux-image-generic				install
linux-libc-dev:i386				install
linux-sound-base				install
localechooser-data				install
locales						install
lockfile-progs					install
login						install
logrotate					install
lsb-base					install
lsb-release					install
lshw						install
lsof						install
ltrace						install
lupin-casper					install
lvm2						install
make						install
makedev						install
man-db						install
manpages					install
manpages-dev					install
mawk						install
mcp-account-manager-uoa				install
media-player-info				install
memtest86+					install
metacity					install
metacity-common					install
mime-support					install
mlocate						install
mobile-broadband-provider-info			install
modemmanager					install
module-init-tools				install
mount						install
mountall					install
mousetweaks					install
mscompress					install
mtools						install
mtr-tiny					install
multiarch-support				install
nano						install
nautilus					install
nautilus-data					install
nautilus-sendto					install
nautilus-sendto-empathy				install
nautilus-share					install
ncurses-base					install
ncurses-bin					install
net-tools					install
netbase						install
netcat-openbsd					install
network-manager					install
network-manager-gnome				install
network-manager-pptp				install
network-manager-pptp-gnome			install
notify-osd					install
notify-osd-icons				install
ntfs-3g						install
ntpdate						install
nux-tools					install
obex-data-server				install
obexd-client					install
onboard						install
oneconf						install
openprinting-ppds				install
openssh-client					install
openssl						install
os-prober					install
overlay-scrollbar				install
overlay-scrollbar-gtk2:i386			install
overlay-scrollbar-gtk3:i386			install
parted						install
passwd						install
patch						install
patchutils					install
pciutils					install
pcmciautils					install
perl						install
perl-base					install
perl-modules					install
pkg-config					install
plymouth					install
plymouth-label					install
plymouth-theme-ubuntu-logo			install
plymouth-theme-ubuntu-text			install
pm-utils					install
policykit-1					install
policykit-1-gnome				install
policykit-desktop-privileges			install
poppler-data					install
poppler-utils					install
popularity-contest				install
powermgmt-base					install
ppp						install
pppconfig					install
pppoeconf					install
pptp-linux					install
printer-driver-c2esp				install
printer-driver-foo2zjs				install
printer-driver-gutenprint			install
printer-driver-hpcups				install
printer-driver-hpijs				install
printer-driver-min12xxw				install
printer-driver-pnm2ppa				install
printer-driver-postscript-hp			install
printer-driver-ptouch				install
printer-driver-pxljr				install
printer-driver-sag-gdi				install
printer-driver-splix				install
procps						install
protobuf-compiler				install
psmisc						install
pulseaudio					install
pulseaudio-module-bluetooth			install
pulseaudio-module-gconf				install
pulseaudio-module-x11				install
pulseaudio-utils				install
python						install
python-appindicator				install
python-apport					install
python-apt					install
python-apt-common				install
python-aptdaemon				install
python-aptdaemon.gtk3widgets			install
python-cairo					install
python-chardet					install
python-configglue				install
python-cups					install
python-cupshelpers				install
python-dbus					install
python-dbus-dev					install
python-debian					install
python-debtagshw				install
python-defer					install
python-dirspec					install
python-gconf					install
python-gi					install
python-gi-cairo					install
python-gnomekeyring				install
python-gnupginterface				install
python-gobject					install
python-gobject-2				install
python-gst0.10					install
python-gtk2					install
python-httplib2					install
python-ibus					install
python-imaging					install
python-libxml2					install
python-lxml					install
python-mako					install
python-markupsafe				install
python-minimal					install
python-notify					install
python-oauth					install
python-openssl					install
python-pam					install
python-pexpect					install
python-piston-mini-client			install
python-pkg-resources				install
python-problem-report				install
python-protobuf					install
python-pycurl					install
python-pyinotify				install
python-qt4					install
python-qt4-dbus					install
python-renderpm					install
python-reportlab				install
python-reportlab-accel				install
python-serial					install
python-simplejson				install
python-sip					install
python-six					install
python-smbc					install
python-twisted-bin				install
python-twisted-core				install
python-twisted-names				install
python-twisted-web				install
python-ubuntu-sso-client			install
python-ubuntuone-client				install
python-ubuntuone-control-panel			install
python-ubuntuone-storageprotocol		install
python-uno					install
python-xapian					install
python-xdg					install
python-zeitgeist				install
python-zope.interface				install
python2.7					install
python2.7-minimal				install
python3						install
python3-apport					install
python3-apt					install
python3-aptdaemon				install
python3-aptdaemon.gtk3widgets			install
python3-aptdaemon.pkcompat			install
python3-brlapi					install
python3-cairo					install
python3-crypto					install
python3-dbus					install
python3-defer					install
python3-distupgrade				install
python3-gdbm					install
python3-gi					install
python3-gi-cairo				install
python3-httplib2				install
python3-louis					install
python3-lxml					install
python3-minimal					install
python3-oauthlib				install
python3-pkg-resources				install
python3-problem-report				install
python3-pyatspi2				install
python3-pycurl					install
python3-pyicu					install
python3-software-properties			install
python3-speechd					install
python3-update-manager				install
python3-virtkey					install
python3-xkit					install
python3.2					install
python3.2-minimal				install
qdbus						install
qpdf						install
qt-at-spi:i386					install
radeontool					install
rdate						install
readline-common					install
reiserfsprogs					install
remmina						install
remmina-common					install
remmina-plugin-rdp				install
remmina-plugin-vnc				install
remote-login-service				install
resolvconf					install
rfkill						install
rhythmbox					install
rhythmbox-data					install
rhythmbox-mozilla				install
rhythmbox-plugin-cdrecorder			install
rhythmbox-plugin-magnatune			install
rhythmbox-plugin-zeitgeist			install
rhythmbox-plugins				install
rhythmbox-ubuntuone				install
rsync						install
rsyslog						install
rtkit						install
samba-common					install
samba-common-bin				install
sane-utils					install
seahorse					install
sed						install
sensible-utils					install
session-migration				install
sessioninstaller				install
sgml-base					install
shared-mime-info				install
shotwell					install
signon-keyring-extension			install
signon-plugin-oauth2				install
signon-plugin-password				install
signon-ui					install
signond						install
simple-scan					install
smbclient					install
sni-qt:i386					install
software-center					install
software-center-aptdaemon-plugins		install
software-properties-common			install
software-properties-gtk				install
sound-theme-freedesktop				install
speech-dispatcher				install
ssh-askpass-gnome				install
ssl-cert					install
strace						install
sudo						install
syslinux					install
syslinux-common					install
syslinux-legacy					install
system-config-printer-common			install
system-config-printer-gnome			install
system-config-printer-udev			install
sysv-rc						install
sysvinit-utils					install
tar						install
tcpd						install
tcpdump						install
telepathy-gabble				install
telepathy-haze					install
telepathy-idle					install
telepathy-indicator				install
telepathy-logger				install
telepathy-mission-control-5			install
telepathy-salut					install
telnet						install
thin-client-config-agent			install
thunderbird					install
thunderbird-globalmenu				install
thunderbird-gnome-support			install
time						install
toshset						install
totem						install
totem-common					install
totem-mozilla					install
totem-plugins					install
transmission-common				install
transmission-gtk				install
ttf-dejavu-core					install
ttf-indic-fonts-core				install
ttf-punjabi-fonts				install
ttf-ubuntu-font-family				install
ttf-wqy-microhei				install
tzdata						install
ubiquity					install
ubiquity-casper					install
ubiquity-frontend-gtk				install
ubiquity-slideshow-ubuntu			install
ubiquity-ubuntu-artwork				install
ubuntu-artwork					install
ubuntu-desktop					install
ubuntu-docs					install
ubuntu-drivers-common				install
ubuntu-extras-keyring				install
ubuntu-keyring					install
ubuntu-minimal					install
ubuntu-mono					install
ubuntu-release-upgrader-core			install
ubuntu-release-upgrader-gtk			install
ubuntu-settings					install
ubuntu-sounds					install
ubuntu-sso-client				install
ubuntu-sso-client-qt				install
ubuntu-standard					install
ubuntu-system-service				install
ubuntu-wallpapers				install
ubuntu-wallpapers-quantal			install
ubuntuone-client				install
ubuntuone-client-gnome				install
ubuntuone-control-panel				install
ubuntuone-control-panel-qt			install
ubuntuone-couch					install
ucf						install
udev						install
udisks						install
udisks2						install
ufw						install
unattended-upgrades				install
unity						install
unity-asset-pool				install
unity-common					install
unity-greeter					install
unity-lens-applications				install
unity-lens-files				install
unity-lens-gwibber				install
unity-lens-music				install
unity-lens-photos				install
unity-lens-shopping				install
unity-lens-video				install
unity-scope-gdocs				install
unity-scope-musicstores				install
unity-scope-video-remote			install
unity-services					install
unity-webapps-common				install
unity-webapps-service				install
uno-libs3					install
unzip						install
update-inetd					install
update-manager					install
update-manager-core				install
update-notifier					install
update-notifier-common				install
upower						install
upstart						install
ure						install
ureadahead					install
usb-creator-common				install
usb-creator-gtk					install
usb-modeswitch					install
usb-modeswitch-data				install
usbmuxd						install
usbutils					install
user-setup					install
util-linux					install
uuid-runtime					install
vbetool						install
vim-common					install
vim-tiny					install
vino						install
wamerican					install
watershed					install
wget						install
whiptail					install
whoopsie					install
wireless-regdb					install
wireless-tools					install
wodim						install
wpasupplicant					install
x11-apps					install
x11-common					install
x11-session-utils				install
x11-utils					install
x11-xfs-utils					install
x11-xkb-utils					install
x11-xserver-utils				install
xauth						install
xbitmaps					install
xcursor-themes					install
xdg-user-dirs					install
xdg-user-dirs-gtk				install
xdg-utils					install
xdiagnose					install
xfonts-base					install
xfonts-encodings				install
xfonts-mathml					install
xfonts-scalable					install
xfonts-utils					install
xfsprogs					install
xinit						install
xinput						install
xkb-data					install
xml-core					install
xorg						install
xorg-docs-core					install
xserver-common					install
xserver-xorg					install
xserver-xorg-core				install
xserver-xorg-input-all				install
xserver-xorg-input-evdev			install
xserver-xorg-input-mouse			install
xserver-xorg-input-synaptics			install
xserver-xorg-input-vmmouse			install
xserver-xorg-input-wacom			install
xserver-xorg-video-all				install
xserver-xorg-video-ati				install
xserver-xorg-video-cirrus			install
xserver-xorg-video-fbdev			install
xserver-xorg-video-intel			install
xserver-xorg-video-mach64			install
xserver-xorg-video-mga				install
xserver-xorg-video-modesetting			install
xserver-xorg-video-neomagic			install
xserver-xorg-video-nouveau			install
xserver-xorg-video-openchrome			install
xserver-xorg-video-qxl				install
xserver-xorg-video-r128				install
xserver-xorg-video-radeon			install
xserver-xorg-video-s3				install
xserver-xorg-video-savage			install
xserver-xorg-video-siliconmotion		install
xserver-xorg-video-sis				install
xserver-xorg-video-sisusb			install
xserver-xorg-video-tdfx				install
xserver-xorg-video-trident			install
xserver-xorg-video-vesa				install
xserver-xorg-video-vmware			install
xterm						install
xul-ext-ubufox					install
xul-ext-unity					install
xul-ext-websites-integration			install
xz-utils					install
yelp						install
yelp-xsl					install
zeitgeist					install
zeitgeist-core					install
zeitgeist-datahub				install
zenity						install
zenity-common					install
zip						install
zlib1g:i386					install

```



**_This is the situation where recording doesn't work (minimal web install):_**

Alsamixer part 1
[IMG]http://oi50.tinypic.com/e8vnfd.jpg[/IMG]

Alsamixer part 2
[IMG]http://oi49.tinypic.com/2gtuj6h.jpg[/IMG]

Alsamixer part 3
[IMG]http://oi50.tinypic.com/wt6gb9.jpg[/IMG]

Some commands:
```

**root@host:~# [COLOR="red"]ls -hl /dev/snd[/COLOR]**
total 0
drwxr-xr-x 2 root root       60 Oct 28 13:04 by-path
crw-rw---T 1 root audio 116,  7 Oct 28 13:04 controlC0
crw-rw---T 1 root audio 116,  6 Oct 28 13:04 hwC0D0
crw-rw---T 1 root audio 116,  5 Oct 28 13:04 pcmC0D0c
crw-rw---T 1 root audio 116,  4 Oct 28 13:04 pcmC0D0p
crw-rw---T 1 root audio 116,  3 Oct 28 13:04 pcmC0D1p
crw-rw---T 1 root audio 116,  2 Oct 28 13:04 pcmC0D2c
crw-rw---T 1 root audio 116,  1 Oct 28 13:04 seq
crw-rw---T 1 root audio 116, 33 Oct 28 13:04 timer

**root@host:~# [COLOR="red"]arecord -l[/COLOR]**
**** List of CAPTURE Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 2: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
  
**root@host:~# [COLOR="red"]arecord -L[/COLOR]**
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=MID
    HDA Intel MID, ALC662 rev1 Analog
    Default Audio Device
sysdefault:CARD=MID
    HDA Intel MID, ALC662 rev1 Analog
    Default Audio Device
front:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    Front speakers
surround40:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    Direct sample mixing device
dmix:CARD=MID,DEV=2
    HDA Intel MID, ALC662 rev1 Analog
    Direct sample mixing device
dsnoop:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    Direct sample snooping device
dsnoop:CARD=MID,DEV=2
    HDA Intel MID, ALC662 rev1 Analog
    Direct sample snooping device
hw:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    Direct hardware device without any conversions
hw:CARD=MID,DEV=2
    HDA Intel MID, ALC662 rev1 Analog
    Direct hardware device without any conversions
plughw:CARD=MID,DEV=0
    HDA Intel MID, ALC662 rev1 Analog
    Hardware device with all software conversions
plughw:CARD=MID,DEV=2
    HDA Intel MID, ALC662 rev1 Analog
    Hardware device with all software conversions
	
**root@host:~# [COLOR="red"]lsmod[/COLOR]**
Module                  Size  Used by
coretemp               13168  0 
kvm                   357806  0 
i2c_isch               12639  0 
gpio_sch               12928  0 
arc4                   12473  2 
snd_hda_codec_realtek    63356  1 
snd_hda_intel          32515  0 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
microcode              18209  0 
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
rt2800usb              22285  0 
rt2800lib              57144  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              19941  1 rt2800usb
rt2x00lib              48562  3 rt2800usb,rt2800lib,rt2x00usb
snd_seq_midi           13132  0 
mac80211              461161  3 rt2800lib,rt2x00usb,rt2x00lib
psmouse                84843  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13031  0 
lpc_sch                12727  0 
cfg80211              175375  2 rt2x00lib,mac80211
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61991  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13037  0 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
gma500_gfx            187730  1 
drm_kms_helper         45271  1 gma500_gfx
drm                   230463  2 gma500_gfx,drm_kms_helper
i2c_algo_bit           13197  1 gma500_gfx
video                  18847  1 gma500_gfx
lp                     13299  0 
parport                40753  1 lp
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
pata_sch               12700  2 
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
r8169                  55976  0 

```

Installed packages:
```

**root@host:~# [COLOR="red"]dpkg --get-selections[/COLOR]**
accountsservice					install
adduser						install
alsa-base					install
alsa-utils					install
apparmor					install
apt						install
apt-transport-https				install
apt-utils					install
apt-xapian-index				install
aptitude					install
aptitude-common					install
at						install
autoconf					install
automake					install
autotools-dev					install
base-files					install
base-passwd					install
bash						install
bash-completion					install
bind9-host					install
binutils					install
biosdevname					install
bsdmainutils					install
bsdutils					install
build-essential					install
busybox-initramfs				install
busybox-static					install
bzip2						install
ca-certificates					install
checkinstall					install
command-not-found				install
command-not-found-data				install
console-setup					install
consolekit					install
coreutils					install
cpio						install
cpp						install
cpp-4.7						install
crda						install
cron						install
dash						install
dbus						install
debconf						install
debconf-i18n					install
debianutils					install
dictionaries-common				install
diffutils					install
discover					install
discover-data					install
dmidecode					install
dmsetup						install
dnsutils					install
dosfstools					install
dpkg						install
dpkg-dev					install
e2fslibs:i386					install
e2fsprogs					install
ed						install
eject						install
fakeroot					install
fdk-aac						install
ffmpeg						install
file						install
findutils					install
friendly-recovery				install
ftp						install
fuse						install
g++						install
g++-4.7						install
gcc						install
gcc-4.7						install
gcc-4.7-base:i386				install
geoip-database					install
gettext-base					install
gir1.2-glib-2.0					install
git						install
git-man						install
gnupg						install
gpgv						install
grep						install
groff-base					install
grub-common					install
grub-gfxpayload-lists				install
grub-pc						install
grub-pc-bin					install
grub2-common					install
gstreamer0.10-pulseaudio:i386			install
gzip						install
hdparm						install
hostname					install
ifupdown					install
info						install
initramfs-tools					install
initramfs-tools-bin				install
initscripts					install
insserv						install
install-info					install
installation-report				install
iproute						install
iptables					install
iputils-ping					install
iputils-tracepath				install
irqbalance					install
isc-dhcp-client					install
isc-dhcp-common					install
iso-codes					install
kbd						install
keyboard-configuration				install
klibc-utils					install
krb5-locales					install
language-pack-en				install
language-pack-en-base				install
language-pack-gnome-en				install
language-pack-gnome-en-base			install
language-selector-common			install
laptop-detect					install
less						install
libaccountsservice0				install
libacl1:i386					install
libalgorithm-diff-perl				install
libalgorithm-diff-xs-perl			install
libalgorithm-merge-perl				install
libapt-inst1.5:i386				install
libapt-pkg4.12:i386				install
libasn1-8-heimdal:i386				install
libasound2:i386					install
libasound2-dev:i386				install
libasound2-plugins:i386				install
libasprintf0c2:i386				install
libasyncns0:i386				install
libattr1:i386					install
libaudio2:i386					install
libavahi-client-dev				install
libavahi-client3:i386				install
libavahi-common-data:i386			install
libavahi-common-dev				install
libavahi-common3:i386				install
libbind9-80					install
libblkid1:i386					install
libboost-iostreams1.49.0			install
libbsd0:i386					install
libbz2-1.0:i386					install
libc-bin					install
libc-dev-bin					install
libc6:i386					install
libc6-dev:i386					install
libcap-ng0					install
libcap2:i386					install
libck-connector0:i386				install
libclass-accessor-perl				install
libclass-isa-perl				install
libcomerr2:i386					install
libcurl3-gnutls:i386				install
libcwidget3					install
libdb5.1:i386					install
libdbus-1-3:i386				install
libdbus-1-dev					install
libdbus-glib-1-2:i386				install
libdevmapper1.02.1:i386				install
libdiscover2					install
libdns81					install
libdpkg-perl					install
libdrm-intel1:i386				install
libdrm-nouveau1a:i386				install
libdrm-nouveau2:i386				install
libdrm-radeon1:i386				install
libdrm2:i386					install
libedit2:i386					install
libelf1:i386					install
libept1.4.12					install
liberror-perl					install
libexpat1:i386					install
libfaac-dev					install
libfaac0					install
libffi6:i386					install
libfile-fcntllock-perl				install
libflac8:i386					install
libfreetype6:i386				install
libfribidi0:i386				install
libfuse2:i386					install
libgcc1:i386					install
libgcrypt11:i386				install
libgcrypt11-dev					install
libgdbm3:i386					install
libgeoip1:i386					install
libgirepository-1.0-1				install
libgl1-mesa-dri:i386				install
libgl1-mesa-glx:i386				install
libglapi-mesa:i386				install
libglib2.0-0:i386				install
libglib2.0-bin					install
libglib2.0-data					install
libglib2.0-dev					install
libglu1-mesa:i386				install
libgmp10:i386					install
libgnutls-dev					install
libgnutls-openssl27:i386			install
libgnutls26:i386				install
libgnutlsxx27:i386				install
libgomp1:i386					install
libgpac-dev:i386				install
libgpac2:i386					install
libgpg-error-dev				install
libgpg-error0:i386				install
libgssapi-krb5-2:i386				install
libgssapi3-heimdal:i386				install
libgstreamer-plugins-base0.10-0:i386		install
libgstreamer0.10-0:i386				install
libhcrypto4-heimdal:i386			install
libheimbase1-heimdal:i386			install
libheimntlm0-heimdal:i386			install
libhx509-5-heimdal:i386				install
libice6:i386					install
libidn11:i386					install
libio-string-perl				install
libisc83					install
libisccc80					install
libisccfg82					install
libitm1:i386					install
libjack-jackd2-0:i386				install
libjpeg-turbo8:i386				install
libjpeg8:i386					install
libjson0:i386					install
libk5crypto3:i386				install
libkeyutils1:i386				install
libklibc					install
libkms1:i386					install
libkrb5-26-heimdal:i386				install
libkrb5-3:i386					install
libkrb5support0:i386				install
libldap-2.4-2:i386				install
libllvm3.1:i386					install
liblocale-gettext-perl				install
liblockfile-bin					install
liblockfile1:i386				install
libltdl-dev:i386				install
libltdl7:i386					install
liblwres80					install
liblzma5:i386					install
libmagic1:i386					install
libmount1:i386					install
libmp3lame-dev:i386				install
libmp3lame0:i386				install
libmpc2:i386					install
libmpfr4:i386					install
libncurses5:i386				install
libncursesw5:i386				install
libnewt0.52					install
libnfnetlink0					install
libnih-dbus1:i386				install
libnih1:i386					install
libnl-3-200:i386				install
libnl-genl-3-200:i386				install
libnuma1					install
libogg-dev:i386					install
libogg0:i386					install
libopencore-amrnb-dev:i386			install
libopencore-amrnb0:i386				install
libopencore-amrwb-dev:i386			install
libopencore-amrwb0:i386				install
libopus-dev					install
libopus-doc					install
libopus0					install
liborc-0.4-0:i386				install
libp11-kit-dev					install
libp11-kit0:i386				install
libpam-ck-connector:i386			install
libpam-modules:i386				install
libpam-modules-bin				install
libpam-runtime					install
libpam0g:i386					install
libparse-debianchangelog-perl			install
libparted0debian1:i386				install
libpcap0.8:i386					install
libpci3:i386					install
libpciaccess0:i386				install
libpcre3:i386					install
libpcre3-dev					install
libpcrecpp0:i386				install
libpipeline1:i386				install
libplymouth2					install
libpng12-0:i386					install
libpolkit-gobject-1-0:i386			install
libpopt0:i386					install
libprocps0:i386					install
libpulse-dev:i386				install
libpulse-mainloop-glib0:i386			install
libpulse0:i386					install
libpulsedsp:i386				install
libquadmath0:i386				install
libreadline6:i386				install
libroken18-heimdal:i386				install
librtmp-dev					install
librtmp0:i386					install
libsamplerate0:i386				install
libsasl2-2:i386					install
libsasl2-modules:i386				install
libselinux1:i386				install
libsigc++-2.0-0c2a:i386				install
libslang2:i386					install
libsm6:i386					install
libsndfile1:i386				install
libspeexdsp1:i386				install
libsqlite3-0:i386				install
libss2:i386					install
libssl1.0.0:i386				install
libstdc++6:i386					install
libstdc++6-4.7-dev				install
libsub-name-perl				install
libswitch-perl					install
libtasn1-3:i386					install
libtasn1-3-dev					install
libtdb1:i386					install
libtext-charwidth-perl				install
libtext-iconv-perl				install
libtext-wrapi18n-perl				install
libtheora-dev:i386				install
libtheora0:i386					install
libtimedate-perl				install
libtinfo5:i386					install
libtool						install
libtxc-dxtn-s2tc0:i386				install
libudev0:i386					install
libusb-0.1-4:i386				install
libusb-1.0-0:i386				install
libuuid1:i386					install
libvorbis-dev:i386				install
libvorbis0a:i386				install
libvorbisenc2:i386				install
libvorbisfile3:i386				install
libwind0-heimdal:i386				install
libwrap0:i386					install
libx11-6:i386					install
libx11-data					install
libx11-xcb1:i386				install
libxapian22					install
libxau6:i386					install
libxcb-glx0:i386				install
libxcb1:i386					install
libxdamage1:i386				install
libxdmcp6:i386					install
libxext6:i386					install
libxfixes3:i386					install
libxml2:i386					install
libxmuu1:i386					install
libxt6:i386					install
libxtst6:i386					install
libxxf86vm1:i386				install
linux-firmware					install
linux-generic					install
linux-headers-3.5.0-17				install
linux-headers-3.5.0-17-generic			install
linux-headers-generic				install
linux-image-3.5.0-17-generic			install
linux-image-extra-3.5.0-17-generic		install
linux-image-generic				install
linux-libc-dev:i386				install
linux-sound-base				install
locales						install
lockfile-progs					install
login						install
logrotate					install
lsb-base					install
lsb-release					install
lshw						install
lsof						install
ltrace						install
m4						install
make						install
makedev						install
man-db						install
manpages					install
manpages-dev					install
mawk						install
memtest86+					install
mime-support					install
mlocate						install
module-init-tools				install
mount						install
mountall					install
mtr-tiny					install
multiarch-support				install
nano						install
ncurses-base					install
ncurses-bin					install
ncurses-term					install
net-tools					install
netbase						install
netcat-openbsd					install
ntfs-3g						install
ntpdate						install
openssh-client					install
openssh-server					install
openssl						install
opus-tools					install
os-prober					install
parted						install
passwd						install
patch						install
pciutils					install
perl						install
perl-base					install
perl-modules					install
pkg-config					install
plymouth					install
plymouth-theme-ubuntu-text			install
popularity-contest				install
powermgmt-base					install
ppp						install
pppconfig					install
pppoeconf					install
procps						install
psmisc						install
pulseaudio					install
pulseaudio-module-x11				install
pulseaudio-utils				install
python						install
python-apt					install
python-apt-common				install
python-chardet					install
python-debian					install
python-minimal					install
python-six					install
python-xapian					install
python2.7					install
python2.7-minimal				install
python3						install
python3-apt					install
python3-dbus					install
python3-distupgrade				install
python3-gdbm					install
python3-gi					install
python3-minimal					install
python3-update-manager				install
python3.2					install
python3.2-minimal				install
readline-common					install
resolvconf					install
rsync						install
rsyslog						install
rtkit						install
sed						install
sensible-utils					install
sgml-base					install
ssh-import-id					install
strace						install
sudo						install
sysv-rc						install
sysvinit-utils					install
tar						install
tasksel						install
tasksel-data					install
tcpd						install
tcpdump						install
telnet						install
texi2html					install
time						install
tzdata						install
ubuntu-keyring					install
ubuntu-minimal					install
ubuntu-release-upgrader-core			install
ubuntu-standard					install
ucf						install
udev						install
ufw						install
update-manager-core				install
upstart						install
ureadahead					install
usbutils					install
util-linux					install
uuid-runtime					install
vim-common					install
vim-tiny					install
wamerican					install
wbritish					install
wget						install
whiptail					install
wireless-regdb					install
x11-common					install
xauth						install
xkb-data					install
xml-core					install
xz-utils					install
yasm						install
zlib1g:i386					install
zlib1g-dev:i386					install

```





I know this is a lot of text. I found a minor difference with arecord -L:

Left: live-cd (working)
Right: installed ubuntu (mic record not working)

[IMG]http://oi45.tinypic.com/2s9aigw.jpg[/IMG]


Can anyone help me?

---

### Post by jerrrys on 2012-10-28
I wonder if alsa-info-script would help you any

[http://ubuntuforums.org/showthread.php?t=895216](http://ubuntuforums.org/showthread.php?t=895216)

---

### Post by Minimos on 2012-10-28
The output that the alsa-info-script provided me with:

```

**root@fitpc01:~# [COLOR="Red"]wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh[/COLOR]**
--2012-10-28 15:04:39--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org (www.alsa-project.org)... 77.48.224.243
Connecting to www.alsa-project.org (www.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh [following]
--2012-10-28 15:04:39--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh
Resolving git.alsa-project.org (git.alsa-project.org)... 77.48.224.243
Connecting to git.alsa-project.org (git.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-sh]
Saving to: `alsa-info.sh'

    [ <=>                                   ] 27,785      --.-K/s   in 0.07s

2012-10-28 15:04:40 (362 KB/s) - `alsa-info.sh' saved [27785]

WARNING: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release.
ALSA Information Script v 0.4.61
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release.
Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=4d611d3a94cd3d6b30afa0635d5f201b3ed41413

Please inform the person helping you.

```

So the URL is: [http://www.alsa-project.org/db/?f=4d611d3a94cd3d6b30afa0635d5f201b3ed41413](http://www.alsa-project.org/db/?f=4d611d3a94cd3d6b30afa0635d5f201b3ed41413)

I'm not sure what to look at, but I'm digging in the file...


Im going to do the same on the working live-cd, and compare the output. I'll post it here soon.

**Update:**
The output file of the working live-cd can be found here: [http://www.alsa-project.org/db/?f=3a2965b79e070d16350ff7f5824076701fd06e14](http://www.alsa-project.org/db/?f=3a2965b79e070d16350ff7f5824076701fd06e14)

It have to compare more, but it looks like pulseaudio is running on live-cd and not on the installed ubuntu.

**Update 2:**
There are some differences in the two files. **Left is the (not working) installed Ubuntu**. **Right is the working Live-cd**. I see that the Live-cd doesn't have a Digital interface enabled that the installed Ubuntu has enabled. And also pulseaudio is not running on the installed Ubuntu. I'm trying some things out, I'll keep this post up to date; if someone got an idea meanwhile, please do post it here :-)

Screenshot of comparison of the two logs, cut in pieces:
[IMG]http://oi48.tinypic.com/jgi2h3.jpg[/IMG]

The modules that are **running**, mentioned in this log, **on the Live-cd**, and that are **NOT present** in the log of the **installed Ubuntu**:
```

Module
dm_crypt
dm_multipath
scsi_dh
bnep
parport_pc
ppdev
rfcomm
bluetooth
squashfs
overlayfs
nls_iso8859_1
dm_raid45
xor
dm_mirror
dm_region_hash
dm_log
usb_storage

```

**Update 3:**
If I do:
```

pulseaudio -D

```
and then generate the same log file, it pulseaudio is also running. I've tested if I could record the microphone (all on the installed Ubuntu): still no go :'(

---

### Post by Minimos on 2012-10-28
Okay! I found the solution for my problem.

When I ran 'amixer', I came across this:
```

Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 10 [32%] [1.50dB] [**off**]
  Front Right: Capture 10 [32%] [1.50dB] [**off**]

```

This 'off' I tried to change to 'on', with this command:

```

[COLOR="Red"]amixer set 'Capture' toggle[/COLOR]

```

And I tried my basic command:

```

arecord | aplay

```

And I could hear myself speaking! So *yay! Thx for your help on the forums, steering me in the good direction!:guitar:

---

### Post by jerrrys on 2012-10-28
Wow, a phenomenal job on your part  :)

[]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

