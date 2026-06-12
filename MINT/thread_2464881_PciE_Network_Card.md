---
title: "PciE Network Card"
date: 2021-07-15
forum: MINT
---

### Post by azmo35 on 2021-07-15
Hi greetings from Portugal, The reason of this post is to ask for info or views on a new card to replace on board network port so my machine > System:    Kernel: 5.4.0-77-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Cinnamon 4.8.6 
           wm: muffin dm: LightDM Distro: Linux Mint 20.1 Ulyssa base: Ubuntu 20.04 focal 
Machine:   Type: Desktop System: Gigabyte product: N/A v: N/A serial: <filter> Chassis: type: 3 
           serial: <filter> 
           Mobo: Gigabyte model: F2A88X-D3H v: x.x serial: <filter> BIOS: American Megatrends 
           v: F7 date: 12/25/2015 
Battery:   Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M185 serial: <filter> 
           charge: 55% (should be ignored) status: Discharging 
CPU:       Topology: Quad Core model: AMD Athlon X4 880K bits: 64 type: MCP arch: Steamroller 
           rev: 1 L2 cache: 2048 KiB 
           flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm bogomips: 31942 
           Speed: 1936 MHz min/max: 1700/4000 MHz Core speeds (MHz): 1: 1796 2: 1708 3: 1704 
           4: 1704 
Graphics:  Device-1: AMD Baffin [Radeon RX 550 640SP / RX 560/560X] vendor: Gigabyte 
           driver: amdgpu v: kernel bus ID: 01:00.0 chip ID: 1002:67ff 
           Display: x11 server: X.Org 1.20.9 driver: amdgpu,ati unloaded: fbdev,modesetting,vesa 
           resolution: 3840x2160~30Hz 
           OpenGL: 
           renderer: Radeon RX 560 Series (POLARIS11 DRM 3.35.0 5.4.0-77-generic LLVM 11.0.0) 
           v: 4.6 Mesa 20.2.6 direct render: Yes 
Audio:     Device-1: AMD FCH Azalia vendor: Gigabyte driver: snd_hda_intel v: kernel 
           bus ID: 00:14.2 chip ID: 1022:780d 
           Device-2: AMD Baffin HDMI/DP Audio [Radeon RX 550 640SP / RX 560/560X] vendor: Gigabyte 
           driver: snd_hda_intel v: kernel bus ID: 01:00.1 chip ID: 1002:aae0 
           Sound Server: ALSA v: k5.4.0-77-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: Gigabyte 
           driver: r8169 v: kernel port: d000 bus ID: 02:00.0 chip ID: 10ec:8168 
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
           IF-ID-1: tun0 state: unknown speed: 10 Mbps duplex: full mac: N/A  
So the motive of asking for info about network card is I think my on board port is getting bad not a long ago it stopped and yesterday it happen again I try reload older kernel and it not solve the problem, try a live environment Mint 20.02, port lights up but not network, but the thing is is working at the writhing of this 
post. A list from Amazon.es > [https://www.amazon.es/-/pt/dp/B003CFATNI/ref=sr_1_1?dchild=1&keywords=pcie+tarjeta+de+red&qid=1626337279&sr=8-1](https://www.amazon.es/-/pt/dp/B003CFATNI/ref=sr_1_1?dchild=1&keywords=pcie+tarjeta+de+red&qid=1626337279&sr=8-1) ??32bits is this one only for 32bits systems!
> [https://www.amazon.es/-/pt/dp/B0006I02VI/ref=sr_1_3?dchild=1&keywords=pcie+tarjeta+de+red&qid=1626337279&sr=8-3](https://www.amazon.es/-/pt/dp/B0006I02VI/ref=sr_1_3?dchild=1&keywords=pcie+tarjeta+de+red&qid=1626337279&sr=8-3)
> [https://www.amazon.es/-/pt/dp/B07PSGQ4H7/ref=sr_1_10?dchild=1&keywords=pcie+tarjeta+de+red&qid=1626337279&sr=8-10](https://www.amazon.es/-/pt/dp/B07PSGQ4H7/ref=sr_1_10?dchild=1&keywords=pcie+tarjeta+de+red&qid=1626337279&sr=8-10)
> [https://www.amazon.es/-/pt/dp/B00JQ4QV2M/ref=sr_1_18?dchild=1&keywords=pcie+tarjeta+de+red&qid=1626337279&sr=8-18](https://www.amazon.es/-/pt/dp/B00JQ4QV2M/ref=sr_1_18?dchild=1&keywords=pcie+tarjeta+de+red&qid=1626337279&sr=8-18)
> [https://www.amazon.es/-/pt/dp/B078GJ1594/ref=sr_1_2?dchild=1&keywords=pcie+tarjeta+de+red&qid=1626337279&sr=8-2](https://www.amazon.es/-/pt/dp/B078GJ1594/ref=sr_1_2?dchild=1&keywords=pcie+tarjeta+de+red&qid=1626337279&sr=8-2)
Well post some of Amazon high reviews but to be honest I'm more interested on yours recommendation than reviews, please help me to get one that will work for many years until this happens again, thanks for take the time to read this post and help.

---

### Post by TheFu on 2021-07-15
My recommendations are simple for the least hassles.  Use GigE, not slower, not faster.  Get an Intel PRO/1000 NIC that uses either the igb or e1000e drivers.  If the listing doesn't say the driver used under linux, keep looking. Better to be picky BEFORE you have buyer's regret.

I have i210, i211 and 82574L models from Intel. These have been excellent over the years for both Linux and BSD systems. I don't read Portuguese, so didn't see any in your list that said Intel or the specific chips.  Keep looking until you find that. Accept nothing less.

Avoid other brands - unless you plan to get a real server-class NIC, but if you were doing that, you'd already know the vendor of which I'm alluding. They don't have NICs onboard in desktop computers.

Avoid 2.5Gbps NICs. The Linux drivers for those weren't quite ready a few months ago when I last looked going back over a year. If you do get a 2.5Gbps, plan on installing a 1 Gbps NIC too, until the 2.5Gbps drivers actually work well.

A single port, GigE PCIe NIC from Intel should be US$20-$25.  Looking at Amazon prices, seems they are $35-$45 now.

---

### Post by CharlesA on 2021-07-15
> **TheFu said:**
> My recommendations are simple for the least hassles.  Use GigE, not slower, not faster.  Get an Intel PRO/1000 NIC that uses either the igb or e1000e drivers.  If the listing doesn't say the driver used under linux, keep looking. Better to be picky BEFORE you have buyer's regret.

I have i210, i211 and 82574L models from Intel. These have been excellent over the years for both Linux and BSD systems. I don't read Portuguese, so didn't see any in your list that said Intel or the specific chips.  Keep looking until you find that. Accept nothing less.

Just vouching for this.

I've a dual port 1 Gb-E card that is running the Intel Pro/1000 chipset. It's branded IBM, but it's made by them with the Intel chipset.

You can find one like it here:
[https://www.amazon.com/Intel-1000-Dual-Server-Adapter/dp/B000BMZHX2](https://www.amazon.com/Intel-1000-Dual-Server-Adapter/dp/B000BMZHX2)

---

### Post by TheFu on 2021-07-15
Be certain that whatever adapter you get, you have a slot of the correct type.  It would be bad to put a x4 PCIe adapter into a x1 PCIe slot.  Going the other way isn't an issue.  An x1 can go into an x2, x4, x8, or x16 slot.

Read the motherboard manual to 100% certain for which slots you have and if there are any limitations when they are used.  For example, some MBs have x16 and x8 slots, but if bother are used, the x16 only works at x8 speeds.  Also, it would be good to know the bus architecture for the system so you don't overload 1 bus if there are 2 or 3 different buses on the MB.  With servers, card placement to ensure redundant buses are used is important.  With typical home desktops, we don't have that, but there might be special handling of different slots since all those USB ports might share a bus with 1 or 2 slots, but not the others.  Just something to consider and research. 

For a home system without lots of NICs and storage adapters and USB2/3 storage devices connection, this stuff usually doesn't matter much, so don't worry too much.  Just know there's a reason some motherboards are $50, some are $150 and others are $300.

---

### Post by azmo35 on 2021-07-21
Thank you for your input, sorry for the links, so tp-link is a no no although someone in the comments says that is working with Ubuntu 20.04, about Intel PRO/1000> [https://www.amazon.es/-/pt/dp/B00CCIN6CM/ref=sr_1_8?dchild=1&keywords=Intel+PRO%2F1000&qid=1626893181&sr=8-8](https://www.amazon.es/-/pt/dp/B00CCIN6CM/ref=sr_1_8?dchild=1&keywords=Intel+PRO%2F1000&qid=1626893181&sr=8-8) this is the cheapest although don't see why Realtek it is not good I will keep looking but at the moment is still working don't know if upgrade to Mint 20.02 help, so thanks for your comments.

---

### Post by TheFu on 2021-07-21
I've had issues with realtek. The NIC on motherboards failed, so I had to either put an add-in NIC or buy a new motherboard. Many people in these forums have issues with realtek.  Do a little searching not for what works, but for what does not work. You'll see.

I'm anti-TP-link based on personal experience with their stuff, but that's just 1 anecdote, not statistically valid.  The tp-link devices I've had over the years had terrible support - meaning updated firmware ended much too quickly compared to the price paid. The devices worked as specified on the box ... except security faults weren't fixed, so ... they became door stops.

---

### Post by CharlesA on 2021-07-21
> **azmo35 said:**
> Thank you for your input, sorry for the links, so tp-link is a no no although someone in the comments says that is working with Ubuntu 20.04, about Intel PRO/1000 this is the cheapest although don't see why Realtek it is not good I will keep looking but at the moment is still working don't know if upgrade to Mint 20.02 help, so thanks for your comments.

That's got an Intel chipset. Just make sure you have a PCIe x4 slot available on your motherboard. It will fit in a x16 slot, but those are usually for video cards.

---

