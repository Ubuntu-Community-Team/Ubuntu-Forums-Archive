---
title: "Zoom virtual background not working"
date: 2024-03-12
forum: Multimedia Software
---

### Post by claus on 2024-03-12
Hi all,

I am currently not able to add a virtual background (VB) when I'm in a Zoom meeting. My hardware is AMD Ryzen 3 3200G with Radeon Vega Graphics × 4,
my graphics card is NVIDIA GeForce GT 710/PCIe/SSE2. I have 22.04.1 LTS (Jammy Jellyfish) 64-bit installed. There should be a ZoomMedia.ini present, but
not in my system. Can anybody help? I successfully loaded a JPG into Zoom, but the VB doesn't show. :-(

TIA,

Claus

---

### Post by Autodave on 2024-03-13
I have a folder on the desktop that I put my pics in for Zoom.  While in a zoom meeting, right click on your pic, chose "Virtual background", and then point it to that folder and pick the pic you want to use.

---

### Post by claus on 2024-03-14
Thanks Dave, I know how to load a photo into Zoom, but replacing the original background doesn't work :( I read that I have to modify the file ZoomMedia.ini, but I couldn't find this file on my computer.

---

### Post by claus on 2024-03-16
Found ZoomMedia.ini:

> [ENV]
PATH=/usr/lib/zoomvdi-universal-plugin/
BIN=zoom
LD_LIBRARY_PATH=/usr/lib/zoomvdi-universal-plugin/Qt/lib/
SSB_HOME=~/.zoomvdi
CONFIG_PATH=~/.zoomvdi
[LOG]
MAX_FILE_COUNT=10
MAX_FILE_SIZE=30
[FEATURE]
SHAREOFFLOAD=1
VIRTUALBACKGROUND=1
[DEVICE_LOCATION]
ISINOFFICE=1 ;set IsInOffice=1 for office, 0 for home
[OS]
OS_DISTRO=ubuntu

The virtual background still doesn't replace the original background. Solution?

Claus

---

### Post by #&amp;thj^% on 2024-03-16
Hi Claus, this has been a known bug on Jammy.
So if you are using Ubuntu 22, do not download it from Ubuntu Software, just download the "Debian" package directly from the Zoom website: [https://zoom.us/download?os=linux](https://zoom.us/download?os=linux)

Source:[https://community.zoom.com/t5/Meetings/Virtual-background-stopped-working/m-p/157576](https://community.zoom.com/t5/Meetings/Virtual-background-stopped-working/m-p/157576)

---

### Post by claus on 2024-03-16
Hi,

and many thanks for the info.

Claus

P. S.: I removed the old version and installed the new "Debian" version, but the VB feature is still not working. I read in the system requirements that the processor has to have at least 8 cores, and mine has only 4.
Does that mean that I can't use this feature?

---

### Post by #&amp;thj^% on 2024-03-16
> **claus said:**
> 
P. S.: I removed the old version and installed the new "Debian" version, but the VB feature is still not working. I read in the system requirements that the processor has to have at least 8 cores, and mine has only 4.
Does that mean that I can't use this feature?
Dang, it would seem so....that's unfortunate that they have such requirements. (I feel that is pure laziness on the Zoom Team). :(

---

