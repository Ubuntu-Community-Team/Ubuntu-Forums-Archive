---
title: "Mythbuntu box going to sleep...  I think."
date: 2010-09-19
forum: Mythbuntu
---

### Post by eladner on 2010-09-19
I built a new system with a Biostar TH55XE Mobo using the latest Mythbuntu (10.04).  The system works fine, but after several hours, it seems to just freeze or sleep or something.  I've scoured every log I can think of and I can't find any messages about "going to sleep" or anything.  No errors or warnings at all (and I've searched every log under /var/log extensively)

There's nothing that seems to wake it up, either.  Oddly enough, pressing the reset button kills the power instead of rebooting the box.

Starting at the top - is there anything in MythTV that would put the box to sleep? 

Working down the stack, is there anything else that's relevant to check?  I've checked the power management settings and everything seems sane for a non-laptop box that's plugged into the wall 24/7.  

On a whim, I disabled acpid, too, and that didn't seem to make a difference.  (haven't tried turning off acpi at boot time yet).

---

### Post by eladner on 2010-09-20
Oddly enough, if I keep a terminal window open from my desktop to the myth box, it seems to stay awake longer.  Otherwise, it's about two hours before it goes night, night.

---

### Post by ian dobson on 2010-09-21
Hi,

What happens if you start a recording that runs long enough to go over the "sleep period", does the system go to sleep or not?

There is a plugin for mythtv (mythshutdown) that shuts down the backend when no recordings are active/upcomming/no jobs active but that wouldn't be effected by opening a terminal window.

I would first check in the bios if there is anything, then maybe in your /var/log directory (syslog) to see if anything "interesting" is listed. Linux is usually quite talkative when you know where to look.

Regards
Ian Dobson

---

### Post by eladner on 2010-09-21
I haven't had the "recording something then the sleep time period occurs" event yet.  I'd have to set something up.  I haven't scheduled a lot of shows yet since the box is still acting flaky with the going to sleep thing.

Yeah, I know about all the logs.  I'm a HP-UX and Solaris admin at work and I've been using Linux since the days it came on floppies, so I'm familiar with all the logging spots.  

I didn't think about the BIOS, though.  I'll check that.  Thanks.

---

### Post by eladner on 2010-09-23
Saw some interesting stuff in the syslog today, and things seem to be hosed up (although my ssh terminal still work).  Any ideas?

```

Sep 23 07:28:56 mythtv kernel: [334768.259474] __ratelimit: 12 callbacks suppressed
Sep 23 07:28:56 mythtv kernel: [334768.259477] hald[1530]: segfault at 0 ip (null) sp bfef274c error 14 in hald[8048000+50000]
Sep 23 07:29:00 mythtv kernel: [334772.904662] mythfrontend.re[1492]: segfault at bff2ba87 ip b44d1283 sp bfa9c6d8 error 4
Sep 23 07:29:00 mythtv kernel: [334772.904680] kernel tried to execute NX-protected page - exploit attempt? (uid: 1000)
Sep 23 07:29:00 mythtv kernel: [334772.904682] BUG: unable to handle kernel paging request at f751a800
Sep 23 07:29:00 mythtv kernel: [334772.904684] IP: [<f751a800>] 0xf751a800
Sep 23 07:29:00 mythtv kernel: [334772.904688] *pdpt = 0000000000893001 *pde = 80000000374001e3 
Sep 23 07:29:00 mythtv kernel: [334772.904691] Oops: 0011 [#1] SMP 
Sep 23 07:29:00 mythtv kernel: [334772.904693] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/irq
Sep 23 07:29:00 mythtv kernel: [334772.904695] Modules linked in: ftdi_sio snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device dv1394 usbserial ppdev parport_pc hdpvr v4l2_common videodev v4l1_compat fbcon psmouse tileblit font serio_raw bitblit softcursor snd raw1394 nvidia(P) vga16fb vgastate soundcore snd_page_alloc intel_agp agpgart lp parport hid_logitech ff_memless ohci1394 usbhid hid ieee1394 r8169 mii pata_jmicron
Sep 23 07:29:00 mythtv kernel: [334772.904717] 
Sep 23 07:29:00 mythtv kernel: [334772.904719] Pid: 1492, comm: mythfrontend.re Tainted: P           (2.6.32-24-generic-pae #43-Ubuntu) TH55XE
Sep 23 07:29:00 mythtv kernel: [334772.904721] EIP: 0060:[<f751a800>] EFLAGS: 00010286 CPU: 2
Sep 23 07:29:00 mythtv kernel: [334772.904723] EIP is at 0xf751a800
Sep 23 07:29:00 mythtv kernel: [334772.904724] EAX: f710f188 EBX: f2a45f88 ECX: 00001000 EDX: f4882000
Sep 23 07:29:00 mythtv kernel: [334772.904725] ESI: f751a800 EDI: f2a45f80 EBP: f2bd9ef4 ESP: f2bd9ec4
Sep 23 07:29:00 mythtv kernel: [334772.904727]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Sep 23 07:29:00 mythtv kernel: [334772.904729] Process mythfrontend.re (pid: 1492, ti=f2bd8000 task=f2980000 task.ti=f2bd8000)
Sep 23 07:29:00 mythtv kernel: [334772.904730] Stack:
Sep 23 07:29:00 mythtv kernel: [334772.904731]  c02242b9 00000000 00000000 000000d0 c07da180 c07d9280 f253c688 c06e69ed
Sep 23 07:29:00 mythtv kernel: [334772.904735] <0> f2a45f80 f253c688 c06e69ed f2a45f80 f2bd9f24 c01eb4eb c07a6780 f2bd9f1c
Sep 23 07:29:00 mythtv kernel: [334772.904738] <0> 0d7d8f3c bff2ba87 00000004 b44d1283 f4882000 bff2ba87 00000004 f2bd9fb4
Sep 23 07:29:00 mythtv kernel: [334772.904742] Call Trace:
Sep 23 07:29:00 mythtv kernel: [334772.904747]  [<c02242b9>] ? d_path+0x29/0xd0
Sep 23 07:29:00 mythtv kernel: [334772.904750]  [<c01eb4eb>] ? print_vma_addr+0x9b/0xf0
Sep 23 07:29:00 mythtv kernel: [334772.904754]  [<c0132008>] ? __bad_area_nosemaphore+0x148/0x160
Sep 23 07:29:00 mythtv kernel: [334772.904756]  [<c0132080>] ? bad_area+0x40/0x50
Sep 23 07:29:00 mythtv kernel: [334772.904760]  [<c05b58b2>] ? do_page_fault+0x332/0x3a0
Sep 23 07:29:00 mythtv kernel: [334772.904762]  [<c05b5580>] ? do_page_fault+0x0/0x3a0
Sep 23 07:29:00 mythtv kernel: [334772.904764]  [<c05b3543>] ? error_code+0x73/0x80
Sep 23 07:29:00 mythtv kernel: [334772.904766] Code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 <00> ba d9 f6 00 64 65 f7 01 00 80 00 00 10 00 00 0c 01 00 00 ff 
Sep 23 07:29:00 mythtv kernel: [334772.904785] EIP: [<f751a800>] 0xf751a800 SS:ESP 0068:f2bd9ec4
Sep 23 07:29:00 mythtv kernel: [334772.904788] CR2: 00000000f751a800
Sep 23 07:29:00 mythtv kernel: [334772.904790] ---[ end trace 1304ed767641e48b ]---
Sep 23 07:29:00 mythtv kernel: [334773.182972] xfwm4: Corrupted page table at address b6aa97b8
Sep 23 07:29:00 mythtv kernel: [334773.182974] *pdpt = 0000000032420001 *pde = 00000091366c2067 
Sep 23 07:29:00 mythtv kernel: [334773.182977] Bad pagetable: 000d [#2] SMP 
Sep 23 07:29:00 mythtv kernel: [334773.182979] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/irq
Sep 23 07:29:00 mythtv kernel: [334773.182981] Modules linked in: ftdi_sio snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device dv1394 usbserial ppdev parport_pc hdpvr v4l2_common videodev v4l1_compat fbcon psmouse tileblit font serio_raw bitblit softcursor snd raw1394 nvidia(P) vga16fb vgastate soundcore snd_page_alloc intel_agp agpgart lp parport hid_logitech ff_memless ohci1394 usbhid hid ieee1394 r8169 mii pata_jmicron

```

... (more of the same) ...

---

### Post by eladner on 2010-09-24
Just to be sure, I ran memtest for at least two full passes before I had to turn the box off ('bout an hour of continuous memory writing/reading/testing).  No errors were reported.

---

### Post by ian dobson on 2010-09-24
Hi,

Are you running autobuilds/weekly builds (version 23.1)? If yes do an update. If not upgrade to the auto builds mythtv package.

Regards
Ian Dobson

---

### Post by eladner on 2010-09-25
Think I found it.   Bad memory.  I let the memtest run several passes and it started getting errors after about the 3rd or 4th pass.

Thx all.

---

### Post by nickrout on 2010-09-26
> **eladner said:**
> Think I found it.   Bad memory.  I let the memtest run several passes and it started getting errors after about the 3rd or 4th pass.

Thx all.

Is your system overheating, resulting in the mem error. Just thinking that it takes a while to show up so could be heat related.

---

