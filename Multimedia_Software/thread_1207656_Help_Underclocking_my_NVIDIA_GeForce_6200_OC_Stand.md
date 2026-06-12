---
title: "Help Underclocking my NVIDIA GeForce 6200 OC Standard PCI edition!"
date: 2009-07-08
forum: Multimedia Software
---

### Post by DaGrimReefah on 2009-07-08
Hello. I have an Intel 2.8 GHz Pentium 4 with an NVidia GeForce 6200 OC, standard PCI version. With my current FSB speed of 400 MHz, I have to underclock it. I had another computer with the same setup and Ubuntu 8.10, but different motherboard. I had to underclock it on that computer, too, for if I didn't (on either computer), any games or 3D would frequently freeze the computer up for about 15 seconds (Ubuntu or Windows). It worked fine. Now that I am using this other computer and it's different motherboard though, it completely locks up and crashes every time I play games with any kind of OpenGL. I have Windows on a seperate harddrive on this same computer as well. Underclocking works fine in Windows. 

            My friend (who used to own this computer) said he once set a "magic frequency" as he calls it, on both the core and the memory. He of course has since forgotten it, and I am going mad trying to trial and error my way through crashes and hard restarts.

EDIT: My card's base speed is 350 MHz core and 410 MHz memory.
 
Using 
```
sudo dmidecode
```
My mother board is:

```
Base Board Information
	Manufacturer: Dell Computer Corporation
	Product Name: 07W080
	Version: A00
	Serial Number: ..CN7082132NG05K.
```
  
And my processor and FSB information:

```
Handle 0x0005, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Socket 478
	Type: Central Processor
	Family: Pentium 4
	Manufacturer: Intel
	ID: 27 0F 00 00 FF FB EB BF
	Signature: Type 0, Family 15, Model 2, Stepping 7
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
		PBE (Pending break enabled)
	Version: Intel Pentium(R) 4
	Voltage: 0.0 V
	External Clock: 400 MHz
	Max Speed: 2800 MHz
	Current Speed: 2000 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0009
	L2 Cache Handle: 0x000A
	L3 Cache Handle: Not Provided
	Serial Number:  
	Asset Tag:  
	Part Number: 
```

If anyone knows of any GPU underclocking or frequency tweaking guides or have some tips specifically for NVidia GeForce 6200 OC PCI, that would be something of a "miracle" and I can get on enjoying my main harddrive like I used to!

---

### Post by LoloftheRings on 2009-07-08
Maybe you want to try nvclock, install the 'nvclock_gtk' package for an easy interface.
nvclock has to be ran every time you start your box so you might want to create a script for it.

That'd be something like:
[code]
#!/bin/bash
nvclock -m [memory speed]
nvclock -n [gpu speed]
[/code/

then, 'chmod +x [script name]' and put into system->preferences->session (or was it startup applications?)

---

### Post by DaGrimReefah on 2009-07-08
> **LoloftheRings said:**
> Maybe you want to try nvclock, install the 'nvclock_gtk' package for an easy interface.
nvclock has to be ran every time you start your box so you might want to create a script for it.

That'd be something like:
[code]
#!/bin/bash
nvclock -m [memory speed]
nvclock -n [gpu speed]
[/code/

then, 'chmod +x [script name]' and put into system->preferences->session (or was it startup applications?)

It works! Thank you very much LOLOTR for suggesting nvclock, I don't know why I passed that package up! What I did was disabled coolbits, since it just exacerbated the problem. Then I set my frequencies to desired values, and it auto-tuned it for me! Coolbits doesn't do that. I was 0.25 MHz off on my memory speed, just 0.25MHz lol. Regardless, it works flawlessly now. Thank you again.

---

