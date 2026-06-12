---
title: "Access Violation error for The Godfather under Wine"
date: 2010-09-28
forum: Multimedia Software
---

### Post by fifteenrabbits on 2010-09-28
Hey there y'all.

I get this access violation message when I try to run The Godfather in Wine.

The Godfather is an audio file tagging and organization program.

The message reads:

Exception EAccessViolation in module TheGodFather.exe at 00000000.
Access violation at address 00000000. Read of address 00000000.

The header says "Application Error" and my only option is an OK button which terminates the program.

This is the output I get in the command line:


```
wine TheGodFather.exe
err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject no class object {00000514-0000-0010-8000-00aa006d2ea4} could be created for context 0x5
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b845390 (thread 003d), starting debugger...
First chance exception: 0xc0000025 in 32-bit code (0x7bc3b63e).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc3b63e ESP:0032f5e4 EBP:0032f648 EFLAGS:00000282(   - 00      - -IS1)
 EAX:0032f5f0 EBX:7bc8aff4 ECX:0011004c EDX:0032f9c8
 ESI:0032f9c8 EDI:0032f654
Stack dump:
0x0032f5e4:  0032f5fc 0000007b 0032f628 c0000025
0x0032f5f4:  00000001 0032f9c8 0032fa60 00000000
0x0032f604:  00986138 00405469 0098934c 0032f628
0x0032f614:  004054ac 00986134 00986138 005b834c
0x0032f624:  00407829 6f727245 72632072 69746165
0x0032f634:  6f20676e 63656a62 20202e74 7bc3b5f0
Backtrace:
=>1 0x7bc3b63e __regs_RtlRaiseException+0x4e() in ntdll (0x0032f648)
  2 0x7bc7896f in ntdll (+0x6896f) (0x0032f9a8)
  3 0x7bc3a8d6 RtlRaiseException+0x6() in ntdll (0x0032fa20)
  4 0x005bbaab in thegodfather (+0x1bbaab) (0x0032fa60)
  5 0x005bc33b in thegodfather (+0x1bc33b) (0x0032fa98)
  6 0x004260f8 in thegodfather (+0x260f8) (0x0032fac4)
  7 0x00426329 in thegodfather (+0x26329) (0x0032fb1c)
  8 0x004265d6 in thegodfather (+0x265d6) (0x0032fb48)
  9 0x00426515 in thegodfather (+0x26515) (0x0032fb64)
  10 0x0042b8d2 in thegodfather (+0x2b8d2) (0x0032fbec)
  11 0x004247ef in thegodfather (+0x247ef) (0x0032fc0c)
  12 0x00420f6c in thegodfather (+0x20f6c) (0x0032fc30)
  13 0x004210f6 in thegodfather (+0x210f6) (0x0032fd50)
  14 0x00421187 in thegodfather (+0x21187) (0x0032fd80)
  15 0x0042c585 in thegodfather (+0x2c585) (0x0032fec8)
  16 0x004aa278 in thegodfather (+0xaa278) (0x0032feec)
  17 0x006ed776 in thegodfather (+0x2ed776) (0x0032ff08)
  18 0x7b877ed8 in kernel32 (+0x57ed8) (0x0032ffe8)
0x7bc3b63e __regs_RtlRaiseException+0x4e in ntdll: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (95 modules)
PE	  400000-  868000	Export          thegodfather
ELF	60000000-6001d000	Deferred        ld-linux.so.2
ELF	6001d000-60153000	Deferred        libwine.so.1
ELF	60153000-6016c000	Deferred        libpthread.so.0
ELF	6016c000-60170000	Deferred        libdl.so.2
ELF	60170000-60196000	Deferred        libm.so.6
ELF	60196000-6019e000	Deferred        libnss_compat.so.2
ELF	6019e000-601b5000	Deferred        libnsl.so.1
ELF	601b5000-601bf000	Deferred        libnss_nis.so.2
ELF	601bf000-601cb000	Deferred        libnss_files.so.2
ELF	601cb000-6026a000	Deferred        gdi32<elf>
  \-PE	601e0000-6026a000	\               gdi32
ELF	6026a000-602bc000	Deferred        advapi32<elf>
  \-PE	60280000-602bc000	\               advapi32
ELF	602bc000-6031f000	Deferred        rpcrt4<elf>
  \-PE	602d0000-6031f000	\               rpcrt4
ELF	6031f000-6033e000	Deferred        iphlpapi<elf>
  \-PE	60330000-6033e000	\               iphlpapi
ELF	6033e000-60352000	Deferred        libresolv.so.2
ELF	60352000-6036d000	Deferred        version<elf>
  \-PE	60360000-6036d000	\               version
ELF	6036d000-60382000	Deferred        lz32<elf>
  \-PE	60370000-60382000	\               lz32
ELF	60382000-60396000	Deferred        olepro32<elf>
  \-PE	60390000-60396000	\               olepro32
ELF	60396000-60459000	Deferred        comctl32<elf>
  \-PE	603a0000-60459000	\               comctl32
ELF	60459000-6047a000	Deferred        imm32<elf>
  \-PE	60460000-6047a000	\               imm32
ELF	6047a000-6058e000	Deferred        shell32<elf>
  \-PE	60490000-6058e000	\               shell32
ELF	6058e000-605cd000	Deferred        urlmon<elf>
  \-PE	605a0000-605cd000	\               urlmon
ELF	605cd000-6067b000	Deferred        comdlg32<elf>
  \-PE	605d0000-6067b000	\               comdlg32
ELF	6067b000-606f1000	Deferred        libfreetype.so.6
ELF	606f1000-60706000	Deferred        libz.so.1
ELF	60706000-60736000	Deferred        libfontconfig.so.1
ELF	60736000-6075d000	Deferred        libexpat.so.1
ELF	6075d000-607f6000	Deferred        winex11<elf>
  \-PE	60770000-607f6000	\               winex11
ELF	607f6000-607ff000	Deferred        libsm.so.6
ELF	607ff000-60818000	Deferred        libice.so.6
ELF	60818000-6081e000	Deferred        libxxf86vm.so.1
ELF	6081e000-6093b000	Deferred        libx11.so.6
ELF	6093b000-60940000	Deferred        libuuid.so.1
ELF	60940000-6095a000	Deferred        libxcb.so.1
ELF	6095a000-6095e000	Deferred        libxau.so.6
ELF	6095e000-60962000	Deferred        libxinerama.so.1
ELF	60962000-6096c000	Deferred        libxrender.so.1
ELF	6096c000-60974000	Deferred        libxrandr.so.2
ELF	60974000-6097a000	Deferred        libxfixes.so.3
ELF	6097a000-60984000	Deferred        libxcursor.so.1
ELF	60984000-609b7000	Deferred        uxtheme<elf>
  \-PE	60990000-609b7000	\               uxtheme
ELF	609b7000-609fe000	Deferred        libcups.so.2
ELF	609fe000-60a2d000	Deferred        libgssapi_krb5.so.2
ELF	60a2d000-60ac8000	Deferred        libgnutls.so.26
ELF	60ac8000-60ad4000	Deferred        libavahi-common.so.3
ELF	60ad4000-60ae5000	Deferred        libavahi-client.so.3
ELF	60ae5000-60b96000	Deferred        libkrb5.so.3
ELF	60b96000-60bba000	Deferred        libk5crypto.so.3
ELF	60bba000-60bbe000	Deferred        libcom_err.so.2
ELF	60bbe000-60bc2000	Deferred        libkeyutils.so.1
ELF	60bc2000-60bd3000	Deferred        libtasn1.so.3
ELF	60bd3000-60c46000	Deferred        libgcrypt.so.11
ELF	60c46000-60c7f000	Deferred        libdbus-1.so.3
ELF	60c7f000-60c88000	Deferred        librt.so.1
ELF	60c88000-60c8d000	Deferred        libgpg-error.so.0
ELF	60c8d000-60ca7000	Deferred        wnaspi32<elf>
  \-PE	60c90000-60ca7000	\               wnaspi32
ELF	62378000-6241e000	Deferred        ole32<elf>
  \-PE	62390000-6241e000	\               ole32
ELF	624a7000-624ca000	Deferred        mpr<elf>
  \-PE	624b0000-624ca000	\               mpr
ELF	6e18e000-6e234000	Deferred        oleaut32<elf>
  \-PE	6e1a0000-6e234000	\               oleaut32
ELF	71813000-7184b000	Deferred        winspool<elf>
  \-PE	71820000-7184b000	\               winspool
ELF	71f6b000-71fc6000	Deferred        shlwapi<elf>
  \-PE	71f80000-71fc6000	\               shlwapi
ELF	73b49000-73b59000	Deferred        libxext.so.6
ELF	7465b000-747a6000	Deferred        user32<elf>
  \-PE	74680000-747a6000	\               user32
ELF	7638e000-76396000	Deferred        libkrb5support.so.0
ELF	76ad3000-76ad7000	Deferred        libxcomposite.so.1
ELF	76f5a000-770b4000	Deferred        libc.so.6
ELF	7a0cc000-7a0d2000	Deferred        libxdmcp.so.6
ELF	7a345000-7a395000	Deferred        wininet<elf>
  \-PE	7a350000-7a395000	\               wininet
ELF	7b800000-7b93c000	Export          kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca7000	Export          ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
0000000b 
	0000003c    0
	00000038   15
	00000021   15
	0000001c   15
	0000001e   -1
	0000001b   -1
	0000001f   -1
	0000001d   -1
	00000014   -1
	00000013    0
00000009 (D) C:\Program Files\The GodFather\TheGodFather.exe
	0000003d    0 <==
Backtrace:
=>1 0x7bc3b63e __regs_RtlRaiseException+0x4e() in ntdll (0x0032f648)
  2 0x7bc7896f in ntdll (+0x6896f) (0x0032f9a8)
  3 0x7bc3a8d6 RtlRaiseException+0x6() in ntdll (0x0032fa20)
  4 0x005bbaab in thegodfather (+0x1bbaab) (0x0032fa60)
  5 0x005bc33b in thegodfather (+0x1bc33b) (0x0032fa98)
  6 0x004260f8 in thegodfather (+0x260f8) (0x0032fac4)
  7 0x00426329 in thegodfather (+0x26329) (0x0032fb1c)
  8 0x004265d6 in thegodfather (+0x265d6) (0x0032fb48)
  9 0x00426515 in thegodfather (+0x26515) (0x0032fb64)
  10 0x0042b8d2 in thegodfather (+0x2b8d2) (0x0032fbec)
  11 0x004247ef in thegodfather (+0x247ef) (0x0032fc0c)
  12 0x00420f6c in thegodfather (+0x20f6c) (0x0032fc30)
  13 0x004210f6 in thegodfather (+0x210f6) (0x0032fd50)
  14 0x00421187 in thegodfather (+0x21187) (0x0032fd80)
  15 0x0042c585 in thegodfather (+0x2c585) (0x0032fec8)
  16 0x004aa278 in thegodfather (+0xaa278) (0x0032feec)
  17 0x006ed776 in thegodfather (+0x2ed776) (0x0032ff08)
  18 0x7b877ed8 in kernel32 (+0x57ed8) (0x0032ffe8)
```


any ideas?

<3

---

### Post by Yellow Pasque on 2010-09-29
You'll probably have more luck reporting that to wine devs.

---

### Post by fifteenrabbits on 2010-09-29
> **Temüjin said:**
> You'll probably have more luck reporting that to wine devs.

I did just that and got my problem resolved.

Thanks!

<3

---

