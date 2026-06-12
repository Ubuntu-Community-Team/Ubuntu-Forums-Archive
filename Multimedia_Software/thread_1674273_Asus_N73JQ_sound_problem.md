---
title: "Asus N73JQ sound problem"
date: 2011-01-23
forum: Multimedia Software
---

### Post by arnefm on 2011-01-23
Hi.

I recently bought a new notebook, an Asus N73JQ. This notebook has a special sound system called "Bang & Olufsen ICEpower". The first thing I did was to install Ubuntu 64-bit.
After installing and rebooting I am certain that i heard the Ubuntu login sound but ten minutes later when i tried playing music with Spotify all sound was gone. The login sound now gone too. I have tried editing settings in System -> Preferences -> Sound, with no luck. The settings dialog lists two sound devices, "Internal Audio Analog Stereo" and "HDA NVidia Digital Stereo (HDMI)". Sound output device is set to the Internal Analog ** device. I have tried different profiles for this device but nothing seems to work.

Does anyone here have the same notebook/sound system with a working sound configuration?

---

### Post by kenshaw on 2011-01-24
This first part may or may not be necessary:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-drivers-modules-$(uname -r)

This second part is:

echo "options snd-hda-intel model=eeepc-p901" | sudo tee -a /etc/modprobe.d/alsa-base.conf

Reboot. Make sure that in System->Preferences->Sound on the Hardware tab that you have selected the "Internal Audio" and that everything is unmuted.

(I just got this laptop over the weekend. Cheers. This is the only thing that didn't work 100% completely out of the box.)

---

### Post by kenshaw on 2011-01-29
Anyone stumbling on this page for the N73jq should also see this post:

[URL="http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug"]http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug
[/URL]
to fix the suspend operation.

Basically, you need to create a shutdown script to suspend ehci/xhci (USB 3.0).

Put the following script in /etc/pm/sleep.d/20_custom-ehci_hcd 

```

#!/bin/sh

TMPLIST_E=/tmp/ehci-dev-list
TMPLIST_X=/tmp/xhci-dev-list
E_DIR=/sys/bus/pci/drivers/ehci_hcd
X_DIR=/sys/bus/pci/drivers/xhci_hcd
E_BIND=$E_DIR""/bind
E_UNBIND=$E_DIR""/unbind
X_BIND=$X_DIR""/bind
X_UNBIND=$X_DIR""/unbind


#param1 = temp file, param2 = device dir, param3 = unbind 
unbindDev (){
#inspired by http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19    
  echo -n '' > $1
    for i in `ls $2 | egrep '[0-9a-z]+\:[0-9a-z]+\:.*$'`; do
      echo -n "$i" | tee $3
      echo "$i" >> $1
  done
}

#param1 = tem file, param2 = bind
bindDev(){
  [ -f $1 ] || return
  
  for i in `cat $1`; do
    echo -n "$i" | tee $2

  done
  rm $1
}


case "${1}" in
  hibernate|suspend)
    unbindDev $TMPLIST_E $E_DIR $E_UNBIND
    unbindDev $TMPLIST_X $X_DIR $X_UNBIND
        ;;
  resume|thaw)
    bindDev $TMPLIST_E $E_BIND
    bindDev $TMPLIST_X $X_BIND
        ;;
esac


```

Make sure to chmod +x the script afterwards.
```

chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd

```

Suspend should also now work for you.

---

### Post by kenshaw on 2011-02-01
Another quick update:

There is indeed no need for the linux-alsa-drivers-modules-$(uname -r) modules. They work out of the box.

If your splash screen has been messed up due (ie, doesn't look pretty, and is displaying garbled text over dots on black) please see this post:

[http://www.conanblog.me/it/how-to-get-the-high-resolution-for-tty-back-after-nvidia-driver-update-in-ubuntu/]("http://www.conanblog.me/it/how-to-get-the-high-resolution-for-tty-back-after-nvidia-driver-update-in-ubuntu/")

For fixing the splash screen. It works for me on my N73jq with a resolution of 1280x800.

---

