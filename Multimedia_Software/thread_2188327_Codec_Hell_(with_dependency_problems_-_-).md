---
title: "Codec Hell (with dependency problems -_-)"
date: 2013-11-16
forum: Multimedia Software
---

### Post by MissMonicaE on 2013-11-16
Hi, everybody.
I'm running Ubuntu 12.04 LTS. I tried to install the [Spotify client Linux preview]("https://www.spotify.com/us/download/previews/"), and Terminal told me:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 spotify-client : Depends: libxss1 (>= 1:1.2.0) but it is not installable
                  Recommends: libavcodec53 but it is not going to be installed or
                              libavcodec52 but it is not installable or
                              libavcodec-extra-53 but it is not going to be installed or
                              libavcodec-extra-52 but it is not installable
                  Recommends: libavformat53 but it is not going to be installed or
                              libavformat52 but it is not installable or
                              libavformat-extra-53 or
                              libavformat-extra-52 but it is not installable
E: Unable to correct problems, you have held broken packages.
```
I tried
```
sudo apt-get install libavcodec53
```
but I got
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libavcodec53 : Depends: libgsm1 (>= 1.0.13) but it is not installable
                Depends: libmp3lame0 but it is not installable
                Depends: libschroedinger-1.0-0 (>= 1.0.0) but it is not installable
                Depends: libva1 (> 1.0.15~) but it is not installable
                Depends: libvpx1 (>= 1.0.0) but it is not installable
                Depends: libx264-120 but it is not installable
E: Unable to correct problems, you have held broken packages.
```
and when I tried
```
sudo apt-get install libxss1
```
I got
[CODEPackage libxss1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libxss1' has no installation candidate[/CODE]

After some googling, I tried
```
sudo apt-get install ubuntu-restricted-extras
```
which gave me
```
E: Unable to locate package ubuntu-restricted-extras
```

I tried to install various codecs that Terminal recommended, and they all gave me similar warnings. I don't know what's going on, especially since I didn't have this problem with my previous install of the same version (same machine). Any advice?

---

### Post by MissMonicaE on 2013-11-16
Also, I don't know if this is relevant, but 
```
sudo apt-get-update
```
gives me
```
W: GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ca.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by ajgreeny on 2013-11-16
Make sure you have the correct universe repos available and the codecs should be there.  It's worth installing the libav*-extra versions as they allow you to encode some formats that the standard libav* packages can not do.

To solve your gpg error try running commands
```
sudo apt-get clean
sudo cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```
then try installing the packages again.

---

### Post by MissMonicaE on 2013-11-16
Thanks a lot! I have my restricted-extras now. O:)

There's something wrong with shim-signed, though:
```
Setting up shim-signed (1.5~12.04.1+0.4-0ubuntu4) ...
Unrecognized option `--target=x86_64-efi'
Usage: grub-install [OPTION] [install_device]
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --boot-directory=DIR    install GRUB images under the directory DIR/grub
                          instead of the /boot/grub directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-mkrelpath=FILE   use FILE as grub-mkrelpath
  --grub-mkdevicemap=FILE use FILE as grub-mkdevicemap
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --allow-floppy          Make the drive also bootable as floppy 
                          (default for fdX devices). May break on some BIOSes.
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
   --removable             the installation device is removable
   --bootloader-id=ID      the ID of bootloader.
   --uefi-secure-boot      install an image usable with UEFI Secure Boot
                           (only available if the grub-efi-amd64-signed
                           package is installed)
   --no-uefi-secure-boot   do not install an image usable with UEFI Secure
                           Boot, even if the system was currently started
                           using it

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub, and uses grub-setup
to install grub into the boot sector.

Report bugs to <bug-grub@gnu.org>.
dpkg: error processing shim-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libssl0.9.8 (0.9.8o-7ubuntu3.1) ...
Setting up libxss1 (1:1.2.1-2) ...
Setting up spotify-client (1:0.9.4.183.g644e24e.428-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
which apparently is Bug #1249532, and has something to do with my bootloader. Should I worry?

---

### Post by ajgreeny on 2013-11-17
Sorry, I can't help with anything to do with windows or MS things as I do not have any windows OSs and I certainly can't imagine how to deal with those parts of MS that didn't even exist in my day.

---

### Post by MissMonicaE on 2013-11-17
Okay, thank you!

---

