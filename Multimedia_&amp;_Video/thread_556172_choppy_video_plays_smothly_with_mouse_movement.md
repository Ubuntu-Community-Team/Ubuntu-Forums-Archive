---
title: "choppy video plays smothly with mouse movement"
date: 2007-09-21
forum: Multimedia &amp; Video
---

### Post by marc66thomas on 2007-09-21
I have Feisty booting and running but have two smaller issues.

1. When watching a video feed like on cnn or a news site through a browser (streamed) sound only plays smoothly if I move the mouse rapidly. (If I move the mouse fast I get smooth video and smooth clear sound, otherwise. the whole video and audio is very choppy or doesn't play.)

2. video setting are no responding as expected: under system, administration, Screens and graphics, I put in my password, and I get "I you need to have administrative rights to change all screen settings" as if I typed my password incorrectly. I have done this a number of times and typed my password correctly. The screen is not detecting the other monitor and doesn't allow me to make any changes. but it does show the nvida driver in use.

Here is my grub settings for this laptop:
title Ubuntu gutsy (development branch), kernel 2.6.22-11-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-11-generic root=UUID=598aaa58-bab8-4c01-96f9-8fda1a297d72 ro quiet splash noapic irqpoll acpi=off
initrd /boot/initrd.img-2.6.22-11-generic quiet

I'd appreciate any direction or information on either or both issues
Thank you in advance.

---

### Post by MrHippocampus on 2007-09-21
On the second point, for an nvidia card its better to use the "nvidia-settings" program to configure your monitor, displayconfig-gtk is designed for drivers supporting xrandr 1.2 which (to the best of my knowledge) the nvidia driver in gutsy doesn't support.

edit: on the first point you could try using a different embedded media player in your browser such as vlc or mplayer.

---

### Post by marc66thomas on 2007-09-21
> **MrHippocampus said:**
> On the second point, for an nvidia card its better to use the "nvidia-settings" program to configure your monitor, displayconfig-gtk is designed for drivers supporting xrandr 1.2 which (to the best of my knowledge) the nvidia driver in gutsy doesn't support.

edit: on the first point you could try using a different embedded media player in your browser such as vlc or mplayer.

Thanks for the suggestions, both issues
On your first note. It, "nvidia-settings" doesn't show up in my "system, Administration, Menu choices." do I need to add this or am I off base and it's a package that needs to be added to get the functionality?  
I will add the Mplayer to see if it's more effective for playback of video.

---

### Post by MrHippocampus on 2007-09-21
if it doesnt appear in one of the menus like it should, try opening a terminal, type it in and press return.

---

### Post by marc66thomas on 2007-09-23
Works like a charm ! You rock.

---

