---
title: "BD-ROM dropped from BIOS after booting to 9.10. Works fine in Win7."
date: 2010-03-19
forum: Multimedia Software
---

### Post by silentknyght on 2010-03-19
EDIT: should be "U"buntu, not "KU"buntu in the prefix.

(also posted in "Hardware & Laptops" forum, but second thoughts suggested it might be more helpful here)

So, I just purchased a shiny new LG 10x BD-ROM Combo drive. I installed it without problems. The rest of my system consists of:

MSI k9a2 platinum mobo
AMD Phenom 9950
3x SATA HDD
nvidia gtx260

That's probably everything pertinent. I have the SATA HDDs installed on SATA ports 1, 3, 4 (not the promise slots, 5 & 6), and the BD-ROM installed on SATA 2. I don't think that's an issue, though. I did replace a working sony opiartic (sp?) DVD-RW, so I don't suspect any cable issues (for that and for other reasons).

Stepwise, here's what happens:
note: "restart" = "reboot via restart", as opposed to power down & turn back on.

**1.** I turn on the power. BIOS posts that it sees the BD-ROM in the SATA 2 spot.
**2.** I boot into Ubuntu 9.10 (updated with the latest x.20 kernel). It does take a little longer than usual to load between the grub menu and the login.
**3.** After login, the device shows up as cdrom0 in the "Places" menu. Clicking on it returns an error whether a disc is in the drive or not. A**t this point, however, the open/close button on the drive no longer works. Its as if it's lost all power or connection or something.**
**4.** When I restart, BIOS hangs a while while posting. It shows only devices on SATA ports 1, 3, & 4. It's as if the BD-ROM doesn't exist anymore.
**5.** When I boot into Win7, it doesn't see it either.
**6.** Completely power off. Power back on.
**7.** Bios sees the BD-ROM in SATA #2 again, like it never left.
**8.** Booting straight to Win7 allows me to see the drive. The open/close buttons work. It appears to read discs just fine.
**9.** Restarting to Win7: still normal. BIOS still sees it.
**10.** Restarting to 9.10 after having it working in Win7 results in the same thing: BIOS sees it on startup, but after linux loads, I get no drive and it is dropped from the BIOS on subsequent restarts.

Variants on the above steps turn out the same. In every case I've tested thus far, 9.10 will not find my drive and then BIOS will not see the disc afterward until I power off completely.

lspci and lspci -vvnn show nothing... well, technically they show everything BUT the drive.

I'm planning on purchasing a second BD-ROM (different manufacturer, if I can help it), to test later, but I don't have high hopes. It could be a motherboard issue, I suppose, but updating the BIOS from 1.4 to the latest version (1.9) solved nothing. I don't suspect it's the hardware, though, since it works fine in Win7. **I imagine that the culprit is linux/ubuntu, and I need some help figuring out if this is a fixable problem.**

I'm at my wit's end. I've been really, really happy with Ubuntu and linux in general. Ubuntu is my primary OS, with Win7 as my backup in case of emergencies, but I'm seriously considering wiping linux & using Win7 exclusively altogether with this severe hardware issue.

---

### Post by cbecker78 on 2010-03-19
I'm brand new at linux, but a similar problem with my wifi was resolved when I installed the appropriate linux driver...  Don't know if that info will help you or not.

---

### Post by silentknyght on 2010-03-19
> **cbecker78 said:**
> I'm brand new at linux, but a similar problem with my wifi was resolved when I installed the appropriate linux driver...  Don't know if that info will help you or not.

As I continue to investigate the problem, I have gotten a comment that linux appears to be kicking the drive off the SATA bus, which doesn't actually restart itself until a power cycle (for reasons I don't understand), as opposed to a power restart.  I will try to post a dmesg result when I am back at my computer.

---

### Post by silentknyght on 2010-06-17
FWIW, I still have not found any resolution to the problem, and none of the updates to 9.10 downloaded to date have solved it, either.

---

