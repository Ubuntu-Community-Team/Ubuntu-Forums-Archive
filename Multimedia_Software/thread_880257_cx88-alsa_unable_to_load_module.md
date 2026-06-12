---
title: "cx88-alsa unable to load module"
date: 2008-08-04
forum: Multimedia Software
---

### Post by DumDum on 2008-08-04
Hello,

I'm having some trouble loading module cx88-alsa, so I can get sound from my hauppauge hvr-1300. When I do:
> sudo modprobe -f cx88-alsa
I get the following error:
```
FATAL: Error inserting cx88_alsa (/lib/modules/2.6.24-19-generic/ubuntu/media/cx88/cx88-alsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

and logfile shows the following:
```
Aug  5 01:10:22 paulo-desktop kernel: [ 6509.223641] cx88_alsa: no version magic, tainting kernel.
Aug  5 01:10:22 paulo-desktop kernel: [ 6509.223907] cx88_alsa: Unknown symbol videobuf_pci_alloc
Aug  5 01:10:22 paulo-desktop kernel: [ 6509.224237] cx88_alsa: Unknown symbol videobuf_pci_dma_unmap
Aug  5 01:10:22 paulo-desktop kernel: [ 6509.224285] cx88_alsa: Unknown symbol videobuf_pci_dma_map
```

In order to get my hvr-1300 working I had to do the following:
```
sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb
sudo make
sudo make install
```
I suppose I've installed latest v4l, the card works fine now except for the sound.

How can I compile the cx88-alsa module is order to be able to load it correctly?

Thanks,

DumDum

---

### Post by nicoge on 2008-10-13
I have a similar problem compiling drivers for hvr-4000.
Any suggestion?

Thanks,
Nicola

---

### Post by scunc_dvl on 2008-11-03
While installing, the file in bold is obsolete and deleted but v4l will not compile a new cx88-alsa module on the default generic kernel, as I've seen with 8.04. (I highlighted the file in bold for the output of my "sudo make install" for v4l-dvb).

I believe the solution lies in convincing v4l to compile the module, possibly removed because it was buggy...

I used to have sound working with Marcus Rechbergers(sp.) em28xx stuff before my card was moved to v4l, but anyway.. I'm so close to solving this problem with sound, and some other modules that apparantly got mussed like my webcam driver...


```

**sudo make install**
[sudo] password for skunkpimp:
make -C /home/skunkpimp/compiles/v4l-dvb/v4l-dvb/v4l install
make[1]: Entering directory `/home/skunkpimp/compiles/v4l-dvb/v4l-dvb/v4l'
Stripping debug info from files
-e
Removing obsolete files from /lib/modules/2.6.24-21-generic/kernel/drivers/media/video:

-e
Removing obsolete files from /lib/modules/2.6.24-21-generic/kernel/drivers/media/dvb/cinergyT2:

-e
Removing obsolete files from /lib/modules/2.6.24-21-generic/kernel/drivers/media/dvb/frontends:


[B]Hmm... distro kernel with a non-standard place for module backports detected.
Please always prefer to use vanilla upstream kernel with V4L/DVB
I'll try to remove old/obsolete LUM files from /lib/modules/2.6.24-21-generic/ubuntu/media:[/B]
/lib/modules/2.6.24-21-generic/ubuntu/media/au0828/xc5000.ko
/lib/modules/2.6.24-21-generic/ubuntu/media/ov511/ov511.ko
/lib/modules/2.6.24-21-generic/ubuntu/media/saa7134/saa7134-alsa.ko
/lib/modules/2.6.24-21-generic/ubuntu/media/au0828/au8522.ko
**/lib/modules/2.6.24-21-generic/ubuntu/media/cx88/cx88-alsa.ko**
Installing kernel modules under /lib/modules/2.6.24-21-generic/kernel/drivers/media/:
        video/gspca/m5602/: gspca_m5602.ko
        dvb/dvb-usb/: dvb-usb-dtv5100.ko dvb-usb-opera.ko dvb-usb-cxusb.ko
                dvb-usb-vp7045.ko dvb-usb-af9005-remote.ko dvb-usb-ttusb2.ko
                dvb-usb-af9015.ko dvb-usb-dib0700.ko dvb-usb-a800.ko
                dvb-usb-gp8psk.ko dvb-usb-dibusb-common.ko dvb-usb-au6610.ko
                dvb-usb-digitv.ko dvb-usb.ko dvb-usb-dibusb-mc.ko
                dvb-usb-af9005.ko dvb-usb-nova-t-usb2.ko dvb-usb-dtt200u.ko
                dvb-usb-cinergyT2.ko dvb-usb-vp702x.ko dvb-usb-umt-010.ko
                dvb-usb-anysee.ko dvb-usb-dibusb-mb.ko dvb-usb-dw2102.ko
                dvb-usb-gl861.ko dvb-usb-m920x.ko
        video/zoran/: videocodec.ko zr36050.ko zr36016.ko
                zr36060.ko zr36067.ko
        video/cx18/: cx18.ko
        video/cpia2/: cpia2.ko
        dvb/b2c2/: b2c2-flexcop-pci.ko b2c2-flexcop.ko b2c2-flexcop-usb.ko
        video/ivtv/: ivtvfb.ko ivtv.ko
        common/tuners/: tuner-xc2028.ko mt2060.ko tda9887.ko
                mt2131.ko qt1010.ko mt20xx.ko
                tda827x.ko tda18271.ko xc5000.ko
                mxl5007t.ko tea5761.ko tuner-types.ko
                tda8290.ko tuner-simple.ko mt2266.ko
                tea5767.ko mxl5005s.ko
        video/sn9c102/: sn9c102.ko
        dvb/dvb-core/: dvb-core.ko
        video/: videobuf-dma-contig.ko vpx3220.ko videobuf-dma-sg.ko
                bt856.ko upd64083.ko v4l2-compat-ioctl32.ko
                stradis.ko videobuf-core.ko tda9840.ko
                saa7191.ko cx2341x.ko wm8775.ko
                meye.ko w9968cf.ko saa7185.ko
                tuner.ko zr364xx.ko ks0127.ko
                stv680.ko videobuf-dvb.ko tvaudio.ko
                bt866.ko tea6420.ko cafe_ccic.ko
                saa5246a.ko msp3400.ko tcm825x.ko
                wm8739.ko stkwebcam.ko saa5249.ko
                cpia_pp.ko tda7432.ko w9966.ko
                upd64031a.ko ir-kbd-i2c.ko ov511.ko
                tea6415c.ko dabusb.ko bt819.ko
                cpia_usb.ko videodev.ko tda9875.ko
                adv7175.ko mxb.ko vivi.ko
                cs53l32a.ko s2255drv.ko btcx-risc.ko
                se401.ko saa7110.ko saa7115.ko
                saa6588.ko saa7111.ko v4l2-common.ko
                saa7114.ko hexium_orion.ko hexium_gemini.ko
                tvp5150.ko vp27smpx.ko adv7170.ko
                ov7670.ko saa7127.ko m52790.ko
                v4l1-compat.ko videobuf-vmalloc.ko v4l2-int-device.ko
                c-qcam.ko tveeprom.ko cs5345.ko
                saa717x.ko cpia.ko tlv320aic23b.ko
                bw-qcam.ko
        video/cx23885/: cx23885.ko
        dvb/bt8xx/: dst_ca.ko dvb-bt8xx.ko bt878.ko
                dst.ko
        dvb/siano/: sms1xxx.ko
        video/cx25840/: cx25840.ko
        dvb/ttusb-dec/: ttusbdecfe.ko ttusb_dec.ko
        dvb/dm1105/: dm1105.ko
        video/saa7134/: saa6752hs.ko saa7134-empress.ko saa7134-dvb.ko
                saa7134.ko
        dvb/ttpci/: dvb-ttpci.ko budget-patch.ko ttpci-eeprom.ko
                budget-av.ko budget.ko budget-core.ko
                budget-ci.ko
        video/et61x251/: et61x251.ko
        dvb/frontends/: nxt6000.ko dib7000m.ko drx397xD.ko
                s5h1411.ko si21xx.ko au8522.ko
                s5h1420.ko stv0288.ko nxt200x.ko
                mt352.ko s921.ko isl6405.ko
                s5h1409.ko sp887x.ko dibx000_common.ko
                isl6421.ko mt312.ko or51132.ko
                tda1004x.ko dib3000mb.ko lgs8gl5.ko
                dib3000mc.ko itd1000.ko sp8870.ko
                l64781.ko dib7000p.ko ves1x93.ko
                tda8083.ko stb6100.ko dib0070.ko
                ves1820.ko stv0297.ko tda10086.ko
                cx22700.ko zl10353.ko cx24110.ko
                stv0299.ko dvb_dummy_fe.ko cx24123.ko
                lgdt330x.ko dvb-pll.ko lnbp21.ko
                cx22702.ko stb6000.ko lgdt3304.ko
                cx24116.ko tda8261.ko tda10023.ko
                tua6100.ko bcm3510.ko tda10021.ko
                tda10048.ko stb0899.ko or51211.ko
                tda826x.ko af9013.ko
        video/cx88/: cx8802.ko cx8800.ko cx88-blackbird.ko
                cx88xx.ko cx88-vp3054-i2c.ko cx88-dvb.ko
        video/bt8xx/: bttv.ko
        video/gspca/: gspca_pac207.ko gspca_stk014.ko gspca_spca501.ko
                gspca_spca500.ko gspca_mars.ko gspca_spca508.ko
                gspca_t613.ko gspca_sunplus.ko gspca_vc032x.ko
                gspca_spca561.ko gspca_tv8532.ko gspca_spca505.ko
                gspca_spca506.ko gspca_sonixj.ko gspca_zc3xx.ko
                gspca_main.ko gspca_conex.ko gspca_pac7311.ko
                gspca_sonixb.ko gspca_ov519.ko gspca_finepix.ko
                gspca_etoms.ko
        dvb/pluto2/: pluto2.ko
        video/usbvideo/: ibmcam.ko usbvideo.ko vicam.ko
                ultracam.ko konicawc.ko quickcam_messenger.ko
        video/usbvision/: usbvision.ko
        common/: saa7146_vv.ko ir-common.ko saa7146.ko
        video/em28xx/: em28xx-dvb.ko em28xx.ko
        video/pvrusb2/: pvrusb2.ko
        radio/: dsbr100.ko radio-maestro.ko radio-maxiradio.ko
                radio-si470x.ko radio-gemtek-pci.ko radio-mr800.ko
        video/uvc/: uvcvideo.ko
        dvb/ttusb-budget/: dvb-ttusb-budget.ko
        video/pwc/: pwc.ko
        video/zc0301/: zc0301.ko
        video/ovcamchip/: ovcamchip.ko
        video/au0828/: au0828.ko
/sbin/depmod -a 2.6.24-21-generic
make[1]: Leaving directory `/home/skunkpimp/compiles/v4l-dvb/v4l-dvb/v4l'


```


If I have to build the kernel from sources, well so be it, I haven't had to do that since Breezy Badger :P

---

