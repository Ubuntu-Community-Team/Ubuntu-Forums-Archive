---
title: "branding-ubuntu_0.6 &amp; quadrapassel 1:2.32.1-0ubuntu3"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2011-04-07
```
The following packages will be upgraded: 
  branding-ubuntu 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 375 kB of archives. After unpacking 295 kB will be used.
Do you want to continue? [Y/n/?] 
Get:1 http://archive.ubuntu.com/ubuntu/ natty/main branding-ubuntu all 0.6 [375 kB]
Fetched 375 kB in 0s (689 kB/s)      
(Reading database ... 194292 files and directories currently installed.)
Preparing to replace branding-ubuntu 0.5 (using .../branding-ubuntu_0.6_all.deb) ...
Unpacking replacement branding-ubuntu ...
dpkg: error processing /var/cache/apt/archives/branding-ubuntu_0.6_all.deb (--unpack):
 trying to overwrite '/usr/share/gnome-games/quadrapassel/pixmaps/quadrapassel.svg', which is also in package quadrapassel 1:2.32.1-0ubuntu3
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/branding-ubuntu_0.6_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
``````
:~$ cat /usr/share/gnome-games/quadrapassel/pixmaps/quadrapassel.svg
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!-- Generator: Adobe Illustrator 9.0, SVG Export Plug-In  -->
<svg id="svg2" xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#" xmlns="http://www.w3.org/2000/svg" xml:space="preserve" height="1119.6" width="1115.1" version="1.0" xmlns:cc="http://web.resource.org/cc/" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 508.104 383.717" xmlns:dc="http://purl.org/dc/elements/1.1/"><metadata id="metadata36"><rdf:RDF><cc:Work rdf:about=""><dc:format>image/svg+xml</dc:format><dc:type rdf:resource="http://purl.org/dc/dcmitype/StillImage"/></cc:Work></rdf:RDF></metadata><defs id="defs34"><linearGradient id="linearGradient3155"><stop id="stop3157" stop-color="#000" offset="0"/><stop id="stop3159" stop-color="#1c4e90" offset="1"/></linearGradient><linearGradient id="linearGradient3171" y2="190.02" xlink:href="#linearGradient3155" spreadMethod="reflect" gradientUnits="userSpaceOnUse" x2="509.69" gradientTransform="matrix(.97907 0 0 .97465 -437.12 69.55)" y1="190.02" x1="-7.9335"/><linearGradient id="linearGradient3179" y2="59.13" xlink:href="#linearGradient3155" gradientUnits="userSpaceOnUse" x2="96.213" y1="59.13" x1="-.0026446"/></defs>
<rect id="rect2182" stroke-linejoin="miter" stroke-dasharray="none" fill-rule="evenodd" transform="matrix(.00024678 -1 1 .00024902 0 0)" height="502.61" width="505.8" stroke="#002" stroke-linecap="butt" stroke-miterlimit="4" y="3.4479" x="-444.39" stroke-width="6.6765" fill="url(#linearGradient3171)"/><g id="g15043" opacity=".5" fill-rule="nonzero" transform="matrix(4.2945 0 0 3.9349 53.413 -35.338)" fill="url(#linearGradient3179)"><g id="g15045" fill="url(#linearGradient3179)" fill-rule="nonzero"><path id="path15047" d="m86.068 0c-24.602 0-29.217 35.041-15.377 35.041 13.838 0 39.979-35.041 15.377-35.041z"/><path id="path15049" d="m45.217 30.699c7.369 0.45 15.454-28.122 1.604-26.325-13.845 1.797-8.976 25.875-1.604 26.325z"/><path id="path15051" d="m11.445 48.453c5.241-2.307 0.675-24.872-8.237-18.718-8.908 6.155 2.996 21.024 8.237 18.718z"/><path id="path15053" d="m26.212 36.642c6.239-1.272 6.581-26.864-4.545-22.273-11.128 4.592-1.689 23.547 4.545 22.273z"/><path id="path15055" d="m58.791 93.913c1.107 8.457-6.202 12.627-13.36 7.177-22.787-17.347 37.729-26.002 33.74-49.704-3.311-19.674-63.676-13.617-70.55 17.167-4.653 20.821 19.153 49.707 43.993 49.707 12.22 0 26.315-11.03 28.952-25.012 2.014-10.659-23.699-6.388-22.775 0.665z"/></g></g></svg>
```

Since I do not know the contents of „new“ /usr/share/gnome-games/quadrapassel/pixmaps/quadrapassel.svg I'm reluctant to erase it and allow branding to upgrade...

---

### Post by whoop on 2011-04-07
[https://bugs.launchpad.net/ubuntu/+source/branding-ubuntu/+bug/753598](https://bugs.launchpad.net/ubuntu/+source/branding-ubuntu/+bug/753598)

---

### Post by try1t on 2011-04-07
I managed to fix this problem by removing quadrapassel in safe-mode and then updating and upgrading using shell with networking.

```

apt-get remove quadrapassel
apt-get update
apt-get upgrade
reboot

```

EDIT: Btw quadrapassel seems to be a "falling blocks game", so probably nothing to worry about.

---

### Post by zika on 2011-04-07
I did several upgrades in the meantime, and this is the most benign bug I've seen. It shows how good is aptitude (I use that flavour) in handling this kind of errors, nowadays...

---

