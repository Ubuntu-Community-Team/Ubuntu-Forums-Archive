---
title: "mplayer sound/performance issues"
date: 2008-12-21
forum: Multimedia Software
---

### Post by davidself1001 on 2008-12-21
I have two different problems depending on whether I run cli or gui.  In gui mode after approximately 2/3 seconds the video slows down to a crawl.  I am playing a HD video and cpu is reading 99%.  I have compiz running.  Is there anything short of a new PC to fix this issue?  In cli mode video is a bit slow and I have no audio.  By the way I can get audio in gui mode but only if I allow frames to be dropped.

---

### Post by newtolinuxhardy on 2008-12-21
i have no experience in computer software (however i have plenty of experience with computer hardware) but you could attempt to overclock the cpu.  is it a socket 478?  if so i would recommend a minimum of a 2.4 GHz P4 processor.  maybe even up to a 3 GHz like this one [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116027](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116027)

however, if you have a different socket then search newegg.  if you do use newegg make sure that at least 65% of the reveiwers have given the product 5 eggs (i have yet to get a bad part as long as i followed this advice).  or if you don't like newegg there are several other online sites or you could go to a computer store.

---

### Post by davidself1001 on 2008-12-21
Sounds like a good idea.  Dumb question.  How do I find out what socket I have?

---

### Post by newtolinuxhardy on 2008-12-21
run "sudo dmidecode" in the terminal.  then look through the resulting info until you find a line that says "socket designation: xxx xxx"  or if it doesn't appear then find the motherboard manufacturer and type using the same line in the terminal.  then google " (your motherboard manufacturer here) (your motherboard type here) specs" and you should be able to find it.

---

### Post by sloggerkhan on 2008-12-21
there are several issues here. 
1. If you can't use hardware accelerated rendering on 1.4 ghz P4 you will not be able to play some formats/resolutions as they will be too cpu intensive. For example h264 720P or better will probably not play. But 640x480 or 720x480 wmv, for example, should play fine. So the format and bitrate and resolution and needed scaling of the video you are watching may be a factor.

2. Correct audio output and video overlay in use. I recommend smplayer as an mplayer front end. Try it with xv overlay and also audio. If no go, also try with pulse or OSS audion. 

3. Command line mplayer: may need to optimize your choice of options. Could be reason for the failure.

---

### Post by davidself1001 on 2008-12-21
J4K1 is the socket designation for the cpu.  Doesn't sound like 478 but what do I know.

---

### Post by newtolinuxhardy on 2008-12-21
J4K1 is a jumper designation for the board.  all that tells me is that is an ibm board(according to a google search).  look for a section that says base board information and post what the output says.  for example mine says:

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer INC.
	Product Name: KIRIN-V 
	Version: REV 1.xx
	Serial Number: xxxxxxxxxxx

that tells me that ASUS manufactured the board and what product line the board came from.  and also post the processor information.

---

### Post by davidself1001 on 2008-12-21
Below is the info I get for 4=cpu and 2=base board.  Let me know if it helps.

$ sudo dmidecode -t 4
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0004, DMI type 4, 32 bytes
Processor Information
	Socket Designation: J4K1
	Type: Central Processor
	Family: Pentium 4
	Manufacturer: Intel Corporation
	ID: 07 0F 00 00 FF FB EB 3F
	Signature: Type 0, Family 15, Model 0, Stepping 7
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
	Version: Pentium(R) 4                 
	Voltage: 3.0 V
	External Clock: 100 MHz
	Max Speed: 1400 MHz
	Current Speed: 1400 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided

$ sudo dmidecode -t 2

# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Intel Corporation              
	Product Name: D850GB                         
	Version: AAA22957-306           
	Serial Number: IMGB11602557

---

### Post by newtolinuxhardy on 2008-12-21
[http://www.pcstats.com/articleview.cfm?articleID=799](http://www.pcstats.com/articleview.cfm?articleID=799)
[http://www.intel.com/support/motherboards/desktop/d850gb/sb/cs-013248.htm](http://www.intel.com/support/motherboards/desktop/d850gb/sb/cs-013248.htm)

your processor is a socket 423.  according to the information you posted it is running at its absolute maximum speed.  you could benefit greatly from an upgrade.  its max speed is rated at 1400 MHz but with a bios upgrade you could go up to 2.0 GHz (2000 MHz) maximum but only with a new processor because that one is maxed out.  go here [http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=486&lang=eng](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=486&lang=eng) and you should be able to download the latest BIOS version for your board.  you may need to upgrade but i can't tell from the info you supplied.  just download the latest BIOS and when it installs it will tell you if you already have that version.  i'll do a quick newegg search and post if i find any good processors.

---

### Post by davidself1001 on 2008-12-21
How did you figure out it was a 423 from my info?  I'll probably just need to upgrade my system in general.  I have had the PoS since 2001 so I am long overdue.

---

### Post by newtolinuxhardy on 2008-12-21
> **davidself1001 said:**
> How did you figure out it was a 423 from my info?  I'll probably just need to upgrade my system in general.  I have had the PoS since 2001 so I am long overdue.

click on the two links i provided at the top of the previous post.  thats how i knew.  i have also had my computer since 2001.  the difference is that your BIOS is still supported by intel (even though your processor isn't).  my BIOS is not supported but my processor is.  i also couldn't find any socket 423 processors on any of the sites i searched.  ebay might have some but you might need to get a new motherboard.  if you do decide to get a whole new computer i would recommend building one yourself.  sure its harder but it will be cheaper and faster than what you could buy prebuilt.

---

