---
title: "no video on netflix"
date: 2013-04-29
forum: Multimedia Software
---

### Post by davidbattley on 2013-04-29
Hi I running 13.04 on a g6 hp pavillion laptop
 just followed the instructions here [http://www.jeremymorgan.com/tutorials/linux/how-to-netflix-ubuntu-linux/](http://www.jeremymorgan.com/tutorials/linux/how-to-netflix-ubuntu-linux/). everything has installed but when i select a movie to watch i just get a black screen with sound and no video. i have recently switch back to linux after having bought a windows 8 machine and don't want to go though all the trouble of setting up a windows dual boot just for netflix. i'm done with windows but i would really mis neyflix if it didn't run.

---

### Post by bill23 on 2013-08-18
I am getting the same black screen when I try to run Netflix-desktop. i am on a desktop pc running ubuntu 13.04 also.

---

### Post by bill23 on 2013-08-18
i had the idea of doing a complete removal of Netfix-deskop and everything related then re-install using the comandline. it may have been an idea b as it turned out it was not a good one for I still got the black screen an no video. what i did get was an error message stating the the FIrefo.exe had developed serious problems an had to close an to try back later. Here si what i saw when I clicked on the detail button:

0x00341988: int	$3
Modules:
Module	Address			Debug info	Name (128 modules)
PE	  340000-  346000	Export          mozalloc
PE	  400000-  4e2000	Deferred        firefox
PE	  700000-  8d8000	Deferred        nss3
PE	  9f0000-  d19000	Deferred        mozjs
PE	  d20000-  d64000	Deferred        browsercomps
PE	  f00000- 1257000	Deferred        gkmedias
PE	 1260000- 26d9000	Deferred        xul
PE	 35b0000- 35d7000	Deferred        softokn3
PE	 35e0000- 35f7000	Deferred        nssdbm3
PE	 5010000- 505a000	Deferred        freebl3
PE	 5060000- 50bd000	Deferred        nssckbi
PE	10000000-10022000	Deferred        mozglue
PE	78050000-780b9000	Deferred        msvcp100
PE	78aa0000-78b5e000	Deferred        msvcr100
ELF	7b800000-7ba5b000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba5b000	\               kernel32
ELF	7bc00000-7bcd9000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcd9000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e52b000-7e532000	Deferred        libxfixes.so.3
ELF	7e532000-7e53d000	Deferred        libxcursor.so.1
ELF	7e53d000-7e54d000	Deferred        libxi.so.6
ELF	7e54d000-7e551000	Deferred        libxcomposite.so.1
ELF	7e551000-7e55c000	Deferred        libxrandr.so.2
ELF	7e55c000-7e566000	Deferred        libxrender.so.1
ELF	7e566000-7e56c000	Deferred        libxxf86vm.so.1
ELF	7e56c000-7e570000	Deferred        libxinerama.so.1
ELF	7e570000-7e577000	Deferred        libxdmcp.so.6
ELF	7e577000-7e57b000	Deferred        libxau.so.6
ELF	7e57b000-7e59d000	Deferred        libxcb.so.1
ELF	7e59d000-7e5a3000	Deferred        libuuid.so.1
ELF	7e5a3000-7e5bd000	Deferred        libice.so.6
ELF	7e5bd000-7e6f4000	Deferred        libx11.so.6
ELF	7e6f4000-7e706000	Deferred        libxext.so.6
ELF	7e706000-7e70f000	Deferred        libsm.so.6
ELF	7e726000-7e7b8000	Deferred        winex11<elf>
  \-PE	7e730000-7e7b8000	\               winex11
ELF	7e958000-7e980000	Deferred        libexpat.so.1
ELF	7e980000-7e9b9000	Deferred        libfontconfig.so.1
ELF	7e9b9000-7e9d2000	Deferred        libz.so.1
ELF	7e9d2000-7ea6d000	Deferred        libfreetype.so.6
ELF	7ea6d000-7ea87000	Deferred        version<elf>
  \-PE	7ea70000-7ea87000	\               version
ELF	7ea87000-7eaf7000	Deferred        advapi32<elf>
  \-PE	7ea90000-7eaf7000	\               advapi32
ELF	7eaf7000-7ec0f000	Deferred        gdi32<elf>
  \-PE	7eb00000-7ec0f000	\               gdi32
ELF	7ec0f000-7ed6b000	Deferred        user32<elf>
  \-PE	7ec20000-7ed6b000	\               user32
ELF	7ef6b000-7ef78000	Deferred        libnss_files.so.2
ELF	7ef78000-7ef84000	Deferred        libnss_nis.so.2
ELF	7ef84000-7ef9d000	Deferred        libnsl.so.1
ELF	7ef9d000-7efa6000	Deferred        libnss_compat.so.2
ELF	7efa6000-7efe9000	Deferred        libm.so.6
ELF	b5ceb000-b5d13000	Deferred        mpr<elf>
  \-PE	b5cf0000-b5d13000	\               mpr
ELF	b5d13000-b5d8f000	Deferred        wininet<elf>
  \-PE	b5d20000-b5d8f000	\               wininet
ELF	b608f000-b60b1000	Deferred        explorerframe<elf>
  \-PE	b6090000-b60b1000	\               explorerframe
ELF	b6102000-b611f000	Deferred        libgcc_s.so.1
ELF	b6136000-b614d000	Deferred        libresolv.so.2
ELF	b614d000-b6155000	Deferred        libogg.so.0
ELF	b6155000-b6181000	Deferred        libvorbis.so.0
ELF	b6181000-b62f9000	Deferred        libvorbisenc.so.2
ELF	b62f9000-b6349000	Deferred        libflac.so.8
ELF	b6349000-b6350000	Deferred        libasyncns.so.0
ELF	b6350000-b63c4000	Deferred        libsndfile.so.1
ELF	b63c4000-b640e000	Deferred        libdbus-1.so.3
ELF	b640e000-b6500000	Deferred        libasound.so.2
ELF	b6602000-b660c000	Deferred        libwrap.so.0
ELF	b660c000-b6677000	Deferred        libpulsecommon-3.0.so
ELF	b6677000-b6681000	Deferred        libjson.so.0
ELF	b6681000-b66d0000	Deferred        libpulse.so.0
ELF	b66d0000-b6700000	Deferred        winealsa<elf>
  \-PE	b66e0000-b6700000	\               winealsa
ELF	b68a9000-b68b0000	Deferred        libnss_dns.so.2
ELF	b68b0000-b68b4000	Deferred        libnss_mdns4_minimal.so.2
ELF	b68bb000-b68dd000	Deferred        mmdevapi<elf>
  \-PE	b68c0000-b68dd000	\               mmdevapi
ELF	b6951000-b6966000	Deferred        t2embed<elf>
  \-PE	b6960000-b6966000	\               t2embed
ELF	b69ac000-b6a14000	Deferred        dbghelp<elf>
  \-PE	b69b0000-b6a14000	\               dbghelp
ELF	b6a14000-b6b49000	Deferred        oleaut32<elf>
  \-PE	b6a30000-b6b49000	\               oleaut32
ELF	b6b49000-b6bba000	Deferred        setupapi<elf>
  \-PE	b6b50000-b6bba000	\               setupapi
ELF	b6bba000-b6bf0000	Deferred        uxtheme<elf>
  \-PE	b6bc0000-b6bf0000	\               uxtheme
ELF	b6bf0000-b6c15000	Deferred        imm32<elf>
  \-PE	b6c00000-b6c15000	\               imm32
ELF	b6c15000-b6d1b000	Deferred        comctl32<elf>
  \-PE	b6c20000-b6d1b000	\               comctl32
ELF	b6d1b000-b6d95000	Deferred        shlwapi<elf>
  \-PE	b6d30000-b6d95000	\               shlwapi
ELF	b6d95000-b6fc9000	Deferred        shell32<elf>
  \-PE	b6da0000-b6fc9000	\               shell32
ELF	b6fc9000-b6ff6000	Deferred        netapi32<elf>
  \-PE	b6fd0000-b6ff6000	\               netapi32
ELF	b6ff6000-b700a000	Deferred        msimg32<elf>
  \-PE	b7000000-b700a000	\               msimg32
ELF	b700a000-b704d000	Deferred        usp10<elf>
  \-PE	b7010000-b704d000	\               usp10
ELF	b704d000-b7061000	Deferred        psapi<elf>
  \-PE	b7050000-b7061000	\               psapi
ELF	b7061000-b7087000	Deferred        iphlpapi<elf>
  \-PE	b7070000-b7087000	\               iphlpapi
ELF	b7087000-b70bd000	Deferred        ws2_32<elf>
  \-PE	b7090000-b70bd000	\               ws2_32
ELF	b70bd000-b70d9000	Deferred        wsock32<elf>
  \-PE	b70c0000-b70d9000	\               wsock32
ELF	b70d9000-b7104000	Deferred        msacm32<elf>
  \-PE	b70e0000-b7104000	\               msacm32
ELF	b7104000-b7187000	Deferred        rpcrt4<elf>
  \-PE	b7110000-b7187000	\               rpcrt4
ELF	b7187000-b72c5000	Deferred        ole32<elf>
  \-PE	b71a0000-b72c5000	\               ole32
ELF	b72c5000-b7380000	Deferred        winmm<elf>
  \-PE	b72d0000-b7380000	\               winmm
ELF	b7389000-b738e000	Deferred        libdl.so.2
ELF	b738e000-b7541000	Deferred        libc.so.6
ELF	b7542000-b755d000	Deferred        libpthread.so.0
ELF	b7560000-b7567000	Deferred        libasound_module_pcm_pulse.so
ELF	b7567000-b7570000	Deferred        librt.so.1
ELF	b7574000-b7725000	Dwarf           libwine.so.1
ELF	b7727000-b7749000	Deferred        ld-linux.so.2
ELF	b7749000-b774a000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001e    0
	0000001d    0
	00000014    0
	00000010    0

Perhaps some one more knowledgeable can decipher this an lend some explanation an what can be done to correct this problem so we who have Netflix can again enjoy it?

bill23

---

