---
title: "After 'removing' Ubuntu from MacBook it cannot boot to OSX but loads Grub 2"
date: 2016-11-24
forum: Mac OSX
---

### Post by bartvdbraak on 2016-11-24
[COLOR=#242729][FONT=Arial]So, I installed a dual-boot solution for Mac to use Ubuntu for C programming. I used rEFInd to dual boot between OSX and Ubuntu. Now I'm done with my C programming course, I wanted to delete this partition and restore to SingleBoot OSX. I tried removing the Ubuntu partition from Disk Utilities and everything seemed fine, however the partition was still there (disk utility only emptied it to my knowledge) therefore I wanted to check out the Recovery Boot by using Command+R to get into Disk Recovery Utilities, but since then I am unable to boot into OSX Yosemite.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Trying to remove the Ubuntu partition in Disk Utilities probably triggered this.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]These are my options (as far as I know):
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**When normal boot**: It shows me 'Grub 2' with a black/white prompt, I am unfamiliar with this and I found some things on the internet that I tried to boot from Grub into OSX but I can't seem to make it work. - When asking for my partitions(ROOT (hd1+TAB, it gives me these:
[/FONT][/COLOR]
[FONT=courier new]Partition hd1,gpt1: Filesystem type fat - Label 'EFI', UUID 67E3-17ED -
  Partition start at 20KiB - Total size 204800KiB
Partition hd1,gpt2: No known filesystem detected - 
  Partition start at 204820KiB - Total size 234298724KiB
Partition hd1,gpt3: Filesystem type hfsplus - Label 'Recovery HD' - 
  Last modification time 2016-11-24 09:24:50 Thursday, UUID 9b4a0f2de0c6bcdb - 
  Partition start at 234503544KiB- Total size 634768KiB
Partition hd1,gpt4: Filesystem type hfsplus - Label 'Naamloos' - 
  Last modification time 2016-11-24 09:24:50 Thursday, UUID 75f3078817440770 -
  Partition start at 235138312KiB - Total size 9847656.5KiB
error: failure reading sector 0x0 from 'hd0'.[/FONT]

[COLOR=#242729][FONT=Arial]**When recovery boot (CMD+R)**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I get into OS X Recovery with Internet acces, where I can try to connect to a WiFi network, but it doesn't seem to be working. 
When I connect to my own WiFi, it just keeps spinning in loading screen as if it fails to connect (it doesn't crash cause I can still abort the operation).
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**When choosing startup disk boot (OPTION/ALT)**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This gives me a list of bootable disks, but only 'Recovery HD' is in the list. It also gives me the option to connect to WiFi. When choosing Recovery Disk, all seems pretty normal:
- Looks like OSX is loading 
- Loads up OSX startup screen, asking for password (even has my correct user picture) - When given correct password: slowly loads white bar till about half and then suddenly shows a black screen with a white 'Prohibited' sign ( &#8416;)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
If anyone knows any solutions or credible tutorials/articles/videos on how to solve my problem (if only it brings me into some sort of recovery mode that I can use), please let me know![/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
If you need any more information (or pictures), let me know![/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Thanks alot in advance, I am in mild panic at the moment.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
EDIT: I tried Recovery with Internet again on a different WiFi and it took a minute, then it went to blackscreen en now it says; "apple.com/support -2003F"[/FONT][/COLOR]

---

