---
title: "Need help AverTv go 007 fm"
date: 2008-05-01
forum: Multimedia Software
---

### Post by extremetr on 2008-05-01
&#305;'m using hardy 64 bit and &#305; have avertv go 007 fm pci tv card. I istalled tvtime but tvcard did not work. &#305; did everythin on this forum and [http://www.linuxforums.org/forum/suse-linux-help/112495-avermedia-tv-card-not-working-under-suse10-3-a-2.html](http://www.linuxforums.org/forum/suse-linux-help/112495-avermedia-tv-card-not-working-under-suse10-3-a-2.html)  but it did not work please help:(  (sory for my bad english)

lspci -vv 
```

01:0a.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Avermedia Technologies Inc Avermedia AVerTV GO 007 FM
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (63750ns min, 63750ns max)
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at dbfff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=3 PME-

```

---

### Post by extremetr on 2008-05-01
is there anyone:confused:

---

### Post by extremetr on 2008-05-02
why there are so many disagrees pls help:confused:

dmesg
[PHP][  412.403807] saa7134: disagrees about version of symbol videobuf_streamoff
[  412.403817] saa7134: Unknown symbol videobuf_streamoff
[  412.403914] saa7134: disagrees about version of symbol videobuf_poll_stream
[  412.403916] saa7134: Unknown symbol videobuf_poll_stream
[  412.404119] saa7134: disagrees about version of symbol videobuf_dma_free
[  412.404121] saa7134: Unknown symbol videobuf_dma_free
[  412.404198] saa7134: disagrees about version of symbol videobuf_reqbufs
[  412.404200] saa7134: Unknown symbol videobuf_reqbufs
[  412.404368] saa7134: disagrees about version of symbol videobuf_waiton
[  412.404370] saa7134: Unknown symbol videobuf_waiton
[  412.404514] saa7134: disagrees about version of symbol videobuf_dqbuf
[  412.404516] saa7134: Unknown symbol videobuf_dqbuf
[  412.404887] saa7134: disagrees about version of symbol videobuf_stop
[  412.404888] saa7134: Unknown symbol videobuf_stop
[  412.405172] saa7134: Unknown symbol videobuf_queue_pci_init
[  412.405206] saa7134: disagrees about version of symbol videobuf_dma_unmap
[  412.405208] saa7134: Unknown symbol videobuf_dma_unmap
[  412.405243] saa7134: disagrees about version of symbol videobuf_read_stream
[  412.405245] saa7134: Unknown symbol videobuf_read_stream
[  412.405292] saa7134: disagrees about version of symbol videobuf_querybuf
[  412.405294] saa7134: Unknown symbol videobuf_querybuf
[  412.405394] saa7134: disagrees about version of symbol video_unregister_device
[  412.405396] saa7134: Unknown symbol video_unregister_device
[  412.405430] saa7134: disagrees about version of symbol videobuf_qbuf
[  412.405431] saa7134: Unknown symbol videobuf_qbuf
[  412.405515] saa7134: disagrees about version of symbol video_device_alloc
[  412.405517] saa7134: Unknown symbol video_device_alloc
[  412.405550] saa7134: disagrees about version of symbol videobuf_read_one
[  412.405552] saa7134: Unknown symbol videobuf_read_one
[  412.405630] saa7134: disagrees about version of symbol video_register_device
[  412.405632] saa7134: Unknown symbol video_register_device
[  412.405855] saa7134: disagrees about version of symbol videobuf_iolock
[  412.405857] saa7134: Unknown symbol videobuf_iolock
[  412.405932] saa7134: disagrees about version of symbol videobuf_streamon
[  412.405933] saa7134: Unknown symbol videobuf_streamon
[  412.406143] saa7134: disagrees about version of symbol video_device_release
[  412.406144] saa7134: Unknown symbol video_device_release
[  412.406177] saa7134: disagrees about version of symbol videobuf_mmap_mapper
[  412.406179] saa7134: Unknown symbol videobuf_mmap_mapper
[  412.406285] saa7134: disagrees about version of symbol videobuf_cgmbuf
[  412.406287] saa7134: Unknown symbol videobuf_cgmbuf
[  412.406403] saa7134: disagrees about version of symbol videobuf_to_dma
[  412.406404] saa7134: Unknown symbol videobuf_to_dma
[  412.406437] saa7134: disagrees about version of symbol videobuf_mmap_free
[  412.406438] saa7134: Unknown symbol videobuf_mmap_free
[  423.367911] saa7134: disagrees about version of symbol videobuf_streamoff
[  423.367920] saa7134: Unknown symbol videobuf_streamoff
[  423.368016] saa7134: disagrees about version of symbol videobuf_poll_stream
[  423.368018] saa7134: Unknown symbol videobuf_poll_stream
[  423.368221] saa7134: disagrees about version of symbol videobuf_dma_free
[  423.368223] saa7134: Unknown symbol videobuf_dma_free
[  423.368301] saa7134: disagrees about version of symbol videobuf_reqbufs
[  423.368302] saa7134: Unknown symbol videobuf_reqbufs
[  423.368470] saa7134: disagrees about version of symbol videobuf_waiton
[  423.368471] saa7134: Unknown symbol videobuf_waiton
[  423.368616] saa7134: disagrees about version of symbol videobuf_dqbuf
[  423.368617] saa7134: Unknown symbol videobuf_dqbuf
[  423.369000] saa7134: disagrees about version of symbol videobuf_stop
[  423.369001] saa7134: Unknown symbol videobuf_stop
[  423.369269] saa7134: Unknown symbol videobuf_queue_pci_init
[  423.369303] saa7134: disagrees about version of symbol videobuf_dma_unmap
[  423.369305] saa7134: Unknown symbol videobuf_dma_unmap
[  423.369340] saa7134: disagrees about version of symbol videobuf_read_stream
[  423.369342] saa7134: Unknown symbol videobuf_read_stream
[  423.369389] saa7134: disagrees about version of symbol videobuf_querybuf
[  423.369391] saa7134: Unknown symbol videobuf_querybuf
[  423.369491] saa7134: disagrees about version of symbol video_unregister_device
[  423.369493] saa7134: Unknown symbol video_unregister_device
[  423.369527] saa7134: disagrees about version of symbol videobuf_qbuf
[  423.369529] saa7134: Unknown symbol videobuf_qbuf
[  423.369609] saa7134: disagrees about version of symbol video_device_alloc
[  423.369611] saa7134: Unknown symbol video_device_alloc
[  423.369644] saa7134: disagrees about version of symbol videobuf_read_one
[  423.369646] saa7134: Unknown symbol videobuf_read_one
[  423.369724] saa7134: disagrees about version of symbol video_register_device
[  423.369726] saa7134: Unknown symbol video_register_device
[  423.369950] saa7134: disagrees about version of symbol videobuf_iolock
[  423.369951] saa7134: Unknown symbol videobuf_iolock
[  423.370026] saa7134: disagrees about version of symbol videobuf_streamon
[  423.370028] saa7134: Unknown symbol videobuf_streamon
[  423.370237] saa7134: disagrees about version of symbol video_device_release
[  423.370239] saa7134: Unknown symbol video_device_release
[  423.370272] saa7134: disagrees about version of symbol videobuf_mmap_mapper
[  423.370274] saa7134: Unknown symbol videobuf_mmap_mapper
[  423.370380] saa7134: disagrees about version of symbol videobuf_cgmbuf
[  423.370381] saa7134: Unknown symbol videobuf_cgmbuf
[  423.370497] saa7134: disagrees about version of symbol videobuf_to_dma
[  423.370499] saa7134: Unknown symbol videobuf_to_dma
[  423.370531] saa7134: disagrees about version of symbol videobuf_mmap_free
[  423.370533] saa7134: Unknown symbol videobuf_mmap_free
[  423.401875] saa7134_alsa: Unknown symbol saa7134_tvaudio_setmute
[  423.401997] saa7134_alsa: Unknown symbol saa_dsp_writel
[  423.402078] saa7134_alsa: Unknown symbol saa7134_devlist
[  423.402147] saa7134_alsa: disagrees about version of symbol videobuf_dma_free
[  423.402149] saa7134_alsa: Unknown symbol videobuf_dma_free
[  423.402298] saa7134_alsa: Unknown symbol saa7134_pgtable_alloc
[  423.402346] saa7134_alsa: Unknown symbol saa7134_pgtable_build
[  423.402390] saa7134_alsa: Unknown symbol saa7134_pgtable_free
[  423.402434] saa7134_alsa: Unknown symbol saa7134_dmasound_init
[  423.402547] saa7134_alsa: Unknown symbol saa7134_dmasound_exit
[  423.402622] saa7134_alsa: disagrees about version of symbol videobuf_dma_init
[  423.402623] saa7134_alsa: Unknown symbol videobuf_dma_init
[  423.402732] saa7134_alsa: disagrees about version of symbol videobuf_dma_init_kernel
[  423.402734] saa7134_alsa: Unknown symbol videobuf_dma_init_kernel
[  423.402814] saa7134_alsa: Unknown symbol videobuf_pci_dma_unmap
[  423.402920] saa7134_alsa: Unknown symbol videobuf_pci_dma_map
[  423.402968] saa7134_alsa: Unknown symbol saa7134_set_dmabits
[  577.589761] saa7134: disagrees about version of symbol videobuf_streamoff
[  577.589780] saa7134: Unknown symbol videobuf_streamoff
[  577.589884] saa7134: disagrees about version of symbol videobuf_poll_stream
[  577.589887] saa7134: Unknown symbol videobuf_poll_stream
[  577.590124] saa7134: disagrees about version of symbol videobuf_dma_free
[  577.590126] saa7134: Unknown symbol videobuf_dma_free
[  577.590209] saa7134: disagrees about version of symbol videobuf_reqbufs
[  577.590211] saa7134: Unknown symbol videobuf_reqbufs
[  577.590390] saa7134: disagrees about version of symbol videobuf_waiton
[  577.590392] saa7134: Unknown symbol videobuf_waiton
[  577.590547] saa7134: disagrees about version of symbol videobuf_dqbuf
[  577.590549] saa7134: Unknown symbol videobuf_dqbuf
[  577.590943] saa7134: disagrees about version of symbol videobuf_stop
[  577.590944] saa7134: Unknown symbol videobuf_stop
[  577.591227] saa7134: Unknown symbol videobuf_queue_pci_init
[  577.591267] saa7134: disagrees about version of symbol videobuf_dma_unmap
[  577.591270] saa7134: Unknown symbol videobuf_dma_unmap
[  577.591308] saa7134: disagrees about version of symbol videobuf_read_stream
[  577.591309] saa7134: Unknown symbol videobuf_read_stream
[  577.591358] saa7134: disagrees about version of symbol videobuf_querybuf
[  577.591360] saa7134: Unknown symbol videobuf_querybuf
[  577.591464] saa7134: disagrees about version of symbol video_unregister_device
[  577.591465] saa7134: Unknown symbol video_unregister_device
[  577.591500] saa7134: disagrees about version of symbol videobuf_qbuf
[  577.591502] saa7134: Unknown symbol videobuf_qbuf
[  577.591585] saa7134: disagrees about version of symbol video_device_alloc
[  577.591587] saa7134: Unknown symbol video_device_alloc
[  577.591621] saa7134: disagrees about version of symbol videobuf_read_one
[  577.591623] saa7134: Unknown symbol videobuf_read_one
[  577.591702] saa7134: disagrees about version of symbol video_register_device
[  577.591704] saa7134: Unknown symbol video_register_device
[  577.591939] saa7134: disagrees about version of symbol videobuf_iolock
[  577.591941] saa7134: Unknown symbol videobuf_iolock
[  577.592017] saa7134: disagrees about version of symbol videobuf_streamon
[  577.592019] saa7134: Unknown symbol videobuf_streamon
[  577.592234] saa7134: disagrees about version of symbol video_device_release
[  577.592236] saa7134: Unknown symbol video_device_release
[  577.592270] saa7134: disagrees about version of symbol videobuf_mmap_mapper
[  577.592272] saa7134: Unknown symbol videobuf_mmap_mapper
[  577.592379] saa7134: disagrees about version of symbol videobuf_cgmbuf
[  577.592381] saa7134: Unknown symbol videobuf_cgmbuf
[  577.592498] saa7134: disagrees about version of symbol videobuf_to_dma
[  577.592500] saa7134: Unknown symbol videobuf_to_dma
[  577.592533] saa7134: disagrees about version of symbol videobuf_mmap_free
[  577.592535] saa7134: Unknown symbol videobuf_mmap_free
[/PHP]

---

### Post by extremetr on 2008-05-06
up ](*,)

---

### Post by Tom55 on 2008-05-07
I am now getting similar messages from my Compro T300 (saa7134) card.  It has only occurred since I recompiled v4l to get my new Leadtek Winfast USB tuner to work.

Prior to this the saa7134 was being recognised

---

### Post by bvidinli on 2008-05-21
i have same/similar issue,
i have avertv dvb-s hybrid+fm a700,

ubuntu hardy 8.04,
installed dvb drivers from linuxtv site,

but 
saa7134: disagrees about version of symbol videobuf_streamoff 
errors.

any help is welcome..

---

