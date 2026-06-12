---
title: "Can't stream radio in 12.04"
date: 2012-04-30
forum: Multimedia Software
---

### Post by glendavee on 2012-04-30
Just done a clean install of 12.04. When I try to stream radio via Banshee (or Rythmbox) I am told I need gstreamer plug-ins. When I try to install process fails, and here's the error message

[COLOR="Red"]The following packages have unmet dependencies:

gstreamer0.10-plugins-ugly: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is to be installed
                            Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                            Depends: libglib2.0-0 (>= 2.31.2) but 2.32.1-0ubuntu2 is to be installed
                            Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1 is to be installed
                            Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                            Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                            Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                            Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
gstreamer0.10-plugins-ugly:i386: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is to be installed
                                 Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                                 Depends: libglib2.0-0 (>= 2.31.2) but 2.32.1-0ubuntu2 is to be installed
                                 Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1 is to be installed
                                 Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                                 Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                                 Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                                 Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed[/COLOR

Thing is, when I look, these files are already installed eg libgcc1:4.6.3-lubuntu5 is there - same for the rest
Can anyone tell me what's going on?]

---

### Post by shantiq on 2012-04-30
hi there do not know the detail but remember that on new installs


```
sudo apt-get install ubuntu-restricted-extras
```


tends to cover most of those dependencies


maybe give that a whirl:KS

---

### Post by wolfen69 on 2012-04-30
Are all of your repositories enabled? Try also enabling the partner repos and add the medibuntu repos.

---

### Post by glendavee on 2012-04-30
Thanks Shantiq - installing ubuntu-restricted-extras did the trick. (I already had medibuntu repros enabled)

---

