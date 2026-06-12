---
title: "DVB-T problems"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by Ultra Magnus on 2007-07-13
Hi - I got a USB TV tuner (Freecom DVB-T USB) and I can't seem to get it to work (either in Vista or Ubuntu - but for now I'd like to be able to get it to work in Ubuntu)

I've tried a couple of tutorials but I can't seem to make any progress

When I type dmesg i get:[ 8356.528000] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in cold state, will try to load a firmware
[ 8356.572000] dvb-usb: did not find the firmware file. (dvb-usb-wt220u-fc03.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)

So, it obviously detects that it is there - I downloaded the firmware file mentioned and I put it in the folder /lib/firmware but still nothing

I installed Kaffeine but It said that it couldn't detect a dvb device.

Anyone have any ideas?

Thanks!

---

### Post by madsmaddad on 2007-07-19
I have the same DVB-t with the same message  in dmesg:

[ 1071.018999] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) succ                                                              essfully initialized and connected.
[ 1071.019154] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Free                                                              com)' in warm state.
[ 1071.019248] dvb-usb: will use the device's hardware PID filter (table count:                                                               15).
[ 1071.019529] DVB: registering new adapter (WideView WT-220U PenType Receiver (                                                              Typhoon/Freecom)).
[ 1071.019635] DVB: registering frontend 1 (WideView USB DVB-T)...
[ 1071.019923] input: IR-receiver inside an USB DVB receiver as /class/input/inp                                                              ut7
[ 1071.019962] dvb-usb: schedule remote query interval to 300 msecs.
[ 1071.019969] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) succ                                                              essfully initialized and connected.
[ 1071.173373] usbcore: registered new interface driver hiddev
[ 1071.173900] usbcore: registered new interface driver usbhid
[ 1071.174249] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[ 1071.184402] usbcore: registered new interface driver xpad
[ 1071.184848] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[ 1073.317834] dvb-usb: recv bulk message failed: -110

Kaffeine recognises it and has been able to scan the channels. But will not play. The yellow LED on the DVB-T never goes green like it did under XP. 

I have an underlying problem that when I start Kaffeine I get the error 'Can't bid info socket', which I have been unable to resolve as yet. 

So I am in the same position as you. But hope this extra information helps both of us.

---

### Post by madsmaddad on 2007-07-23
OK, I still can't view TV live, But I selected a channel and set kaffeine to record  at a specified time, and it did. I was also able to play back the recording. :confused:

---

### Post by MrHippocampus on 2007-07-23
@Ultra Magnus
Although the output says put it in /lib/firmware, you actually need to put the firmware file in a subdirectory of that folder, you must put the file in a subfolder named the same as your current kernel  ("uname -r" in a terminal will tell you the correct name). Sorry if this is what you've done already but I wasn't sure from your post.

---

### Post by madsmaddad on 2007-12-30
Follow the instructions in [http://www.ubuntuforums.org/showthread.php?t=183297](http://www.ubuntuforums.org/showthread.php?t=183297) 

after loading the firmware from 

[http://www.chandlerfamily.org.uk/files/firmware/](http://www.chandlerfamily.org.uk/files/firmware/)   

Then: 
sudo cp dvb-usb-wt220u-fc03 /lib/firmware/$(uname -r)/ 

If you have done a lot of playing around like I had, then I found that I had to Uninstall Kaffeine, reboot and reinstall it before going through the steps in the forum above. also the prompts have changed  from the time that one was written, so be careful. 

I have my copy of my responses if required. 

Mine is now working fine.

---

### Post by ugm6hr on 2008-01-12
> **madsmaddad said:**
> I have my copy of my responses if required. 


I am just about to start installing my new Freecom USB DVB-T stick.

I would be grateful if you would either paste in or upload a file with your answers.

Thanks.

---

### Post by madsmaddad on 2008-01-19
sudo make config
[sudo] password for peterm:
make -C /home/peterm/v4l-dvb/v4l-dvb/v4l config
make[1]: Entering directory `/home/peterm/v4l-dvb/v4l-dvb/v4l'
/lib/modules/2.6.22-14-generic/build/scripts/kconfig/conf ./Kconfig
*
* Linux Kernel Configuration
*
Enable drivers not supported by this kernel (VIDEO_KERNEL_VERSION) [N/y/?] (NEW)
 n
*
* Multimedia devices
*
Video For Linux (VIDEO_DEV) [M/n/y/?] m
  Enable Video For Linux API 1 (DEPRECATED) (VIDEO_V4L1) [Y/n/?] y
  Enable Video For Linux API 1 compatible Layer (VIDEO_V4L1_COMPAT) [Y/?] y
  *
  * Video capture adapters
  *
  Video capture adapters (VIDEO_CAPTURE_DRIVERS) [Y/n/?] y
    Enable advanced debug functionality (VIDEO_ADV_DEBUG) [Y/n/?] y
    Autoselect pertinent encoders/decoders and other helper chips (VIDEO_HELPER_CHIPS_AUTO) [N/y/?] n
      *
      * Encoders/decoders and other helper chips
      *
      *
      * Audio decoders
      *
      Simple audio decoder chips (VIDEO_TVAUDIO) [M/?] m
      Philips TDA7432 audio processor (VIDEO_TDA7432) [M/n/?] n
      Philips TDA9840 audio processor (VIDEO_TDA9840) [M/n/?] n
      Philips TDA9875 audio processor (VIDEO_TDA9875) [M/n/?] n
      Philips TEA6415C audio processor (VIDEO_TEA6415C) [M/n/?] n
      Philips TEA6420 audio processor (VIDEO_TEA6420) [M/n/?] n
      Micronas MSP34xx audio decoders (VIDEO_MSP3400) [M/?] m
      Cirrus Logic CS5345 audio ADC (VIDEO_CS5345) [M/n/?] n
      Cirrus Logic CS53L32A audio ADC (VIDEO_CS53L32A) [M/?] m
      Mitsubishi M52790 A/V switch (VIDEO_M52790) [M/?] m
      Texas Instruments TLV320AIC23B audio codec (VIDEO_TLV320AIC23B) [M/n/?] n
      Wolfson Microelectronics WM8775 audio ADC with input mixer (VIDEO_WM8775) [M/?] m
      Wolfson Microelectronics WM8739 stereo audio ADC (VIDEO_WM8739) [M/?] m
      Panasonic VP27s internal MPX (VIDEO_VP27SMPX) [M/?] m
      *
      * Video decoders
      *
      BT819A VideoStream decoder (VIDEO_BT819) [M/n/?] n
      BT856 VideoStream decoder (VIDEO_BT856) [M/n/?] n
      BT866 VideoStream decoder (VIDEO_BT866) [M/n/?] n
      KS0127 video decoder (VIDEO_KS0127) [M/n/?] n
      OmniVision OV7670 sensor support (VIDEO_OV7670) [M/?] m
      TCM825x camera sensor support (VIDEO_TCM825X) [M/n/?] n
      Philips SAA7110 video decoder (VIDEO_SAA7110) [M/?] m
      Philips SAA7111 video decoder (VIDEO_SAA7111) [M/n/?] n
      Philips SAA7114 video decoder (VIDEO_SAA7114) [M/n/?] n
      Philips SAA7113/4/5 video decoders (VIDEO_SAA711X) [M/?] m
      Philips SAA7191 video decoder (VIDEO_SAA7191) [M/n/?] n
      Texas Instruments TVP5150 video decoder (VIDEO_TVP5150) [M/n/?] n
      vpx3220a, vpx3216b & vpx3214c video decoders (VIDEO_VPX3220) [M/n/?] n
      *
      * Video and audio decoders
      *
      Conexant CX2584x audio/video decoders (VIDEO_CX25840) [M/?] m
      *
      * MPEG video encoders
      *
      Conexant CX2341x MPEG encoders (VIDEO_CX2341X) [M/?] m
      *
      * Video encoders
      *
      Philips SAA7127/9 digital video encoders (VIDEO_SAA7127) [M/?] m
      Philips SAA7185 video encoder (VIDEO_SAA7185) [M/n/?] n
      Analog Devices ADV7170 video encoder (VIDEO_ADV7170) [M/n/?] n
      Analog Devices ADV7175 video encoder (VIDEO_ADV7175) [M/n/?] n
      *
      * Video improvement chips
      *
      NEC Electronics uPD64031A Ghost Reduction (VIDEO_UPD64031A) [M/?] m
      NEC Electronics uPD64083 3-Dimensional Y/C separation (VIDEO_UPD64083) [M/?] m
    Virtual Video Driver (VIDEO_VIVI) [M/n/?] n
    BT848 Video For Linux (VIDEO_BT848) [M/n/?] n
    Mediavision Pro Movie Studio Video For Linux (VIDEO_PMS) [M/n/?] n
    Quickcam BW Video For Linux (VIDEO_BWQCAM) [M/n/?] n
    QuickCam Colour Video For Linux (EXPERIMENTAL) (VIDEO_CQCAM) [M/n/?] n
    W9966CF Webcam (FlyCam Supra and others) Video For Linux (VIDEO_W9966) [M/n/?] n
    CPiA Video For Linux (VIDEO_CPIA) [M/n/?] n
    CPiA2 Video For Linux (VIDEO_CPIA2) [M/n/?] n
    SAA5246A, SAA5281 Teletext processor (VIDEO_SAA5246A) [M/n/?] n
    SAA5249 Teletext processor (VIDEO_SAA5249) [M/n/?] n
    SAB3036 tuner (TUNER_3036) [M/n/?] n
    Stradis 4:2:2 MPEG-2 video driver  (EXPERIMENTAL) (VIDEO_STRADIS) [M/n/?] n
    Zoran ZR36057/36067 Video For Linux (VIDEO_ZORAN) [M/n/?] n
    Sony Vaio Picturebook Motion Eye Video For Linux (VIDEO_MEYE) [M/n/?] n
    Philips SAA7134 support (VIDEO_SAA7134) [M/n/?] n
    Siemens-Nixdorf 'Multimedia eXtension Board' (VIDEO_MXB) [M/n/?] n
    Philips-Semiconductors 'dpc7146 demonstration board' (VIDEO_DPC) [M/n/?] n
    Hexium HV-PCI6 and Orion frame grabber (VIDEO_HEXIUM_ORION) [M/n/?] n
    Hexium Gemini frame grabber (VIDEO_HEXIUM_GEMINI) [M/n/?] n
    Conexant 2388x (bt878 successor) support (VIDEO_CX88) [M/n/?] n
    Conexant cx23885 (2388x successor) support (VIDEO_CX23885) [M/n/?] n
    Conexant cx23416/cx23415 MPEG encoder/decoder support (VIDEO_IVTV) [M/n/?] n
    Marvell 88ALP01 (Cafe) CMOS Camera Controller support (VIDEO_CAFE_CCIC) [M/n/?] n
    *
    * V4L USB devices
    *
    V4L USB devices (V4L_USB_DRIVERS) [Y/n]
      Hauppauge WinTV-PVR USB2 support (VIDEO_PVRUSB2) [M/n/?] n
      Empia EM2800/2820/2840 USB video capture support (VIDEO_EM28XX) [M/n/?] n
      USB video devices based on Nogatech NT1003/1004/1005 (VIDEO_USBVISION) [M/n/?] n
      USB 3com HomeConnect (aka vicam) support (EXPERIMENTAL) (USB_VICAM) [M/n/?] n
      USB IBM (Xirlink) C-it Camera support (USB_IBMCAM) [M/n/?] n
      USB Konica Webcam support (USB_KONICAWC) [M/n/?] n
      USB Logitech Quickcam Messenger (USB_QUICKCAM_MESSENGER) [M/n/?] n
      USB ET61X[12]51 PC Camera Controller support (USB_ET61X251) [M/n/?] n
      OmniVision Camera Chip support (VIDEO_OVCAMCHIP) [M/?] m
      USB W996[87]CF JPEG Dual Mode Camera support (USB_W9968CF) [M/n/?] n
      USB OV511 Camera support (USB_OV511) [M/n/?] n
      USB SE401 Camera support (USB_SE401) [M/n/?] n
      USB SN9C1xx PC Camera Controller support (USB_SN9C102) [M/n/?] n
      USB STV680 (Pencam) Camera support (USB_STV680) [M/n/?] n
      USB ZC0301[P] Image Processor and Control Chip support (USB_ZC0301) [M/n/?] n
      USB Philips Cameras (USB_PWC) [M/n/?] n
      USB ZR364XX Camera support (USB_ZR364XX) [M/n/?] n
  *
  * Radio Adapters
  *
  Radio Adapters (RADIO_ADAPTERS) [Y/n/?]
    ADS Cadet AM/FM Tuner (RADIO_CADET) [M/n/?] n
    AIMSlab RadioTrack (aka RadioReveal) support (RADIO_RTRACK) [M/n/?] n
    AIMSlab RadioTrack II support (RADIO_RTRACK2) [M/n/?] n
    Aztech/Packard Bell Radio (RADIO_AZTECH) [M/n/?] n
    GemTek Radio card (or compatible) support (RADIO_GEMTEK) [M/n/?] n
    GemTek PCI Radio Card support (RADIO_GEMTEK_PCI) [M/n/?] n
    Guillemot MAXI Radio FM 2000 radio (RADIO_MAXIRADIO) [M/n/?] n
    Maestro on board radio (RADIO_MAESTRO) [M/n/?] n
    SF16FMI Radio (RADIO_SF16FMI) [M/n/?] n
    SF16FMR2 Radio (RADIO_SF16FMR2) [M/n/?] n
    TerraTec ActiveRadio ISA Standalone (RADIO_TERRATEC) [M/n/?] n
    Trust FM radio card (RADIO_TRUST) [M/n/?] n
    Typhoon Radio (a.k.a. EcoRadio) (RADIO_TYPHOON) [M/n/?] m
      Support for /proc/radio-typhoon (RADIO_TYPHOON_PROC_FS) [Y/n/?] y
    Zoltrix Radio (RADIO_ZOLTRIX) [M/n/?] n
    D-Link/GemTek USB FM radio support (USB_DSBR) [M/n/?] n
DVB for Linux (DVB_CORE) [M/n/y/?] m
  Load and attach frontend modules as needed (DVB_CORE_ATTACH) [Y/n/?] y
  *
  * DVB/ATSC adapters
  *
  DVB/ATSC adapters (DVB_CAPTURE_DRIVERS) [Y/n/?] y
    *
    * Supported SAA7146 based PCI Adapters
    *
    AV7110 cards (DVB_AV7110) [M/n/?] n
    SAA7146 DVB cards (aka Budget, Nova-PCI) (DVB_BUDGET_CORE) [M/n/?] n
    *
    * Supported USB Adapters
    *
    Support for various USB DVB devices (DVB_USB) [M/n/?] m
      Enable extended debug support for all DVB-USB devices (DVB_USB_DEBUG) [Y/n/?] y
      AVerMedia AverTV DVB-T USB 2.0 (A800) (DVB_USB_A800) [M/n/?] n
      DiBcom USB DVB-T devices (based on the DiB3000M-B) (see help for device list) (DVB_USB_DIBUSB_MB) [M/n/?] n
      DiBcom USB DVB-T devices (based on the DiB3000M-C/P) (see help for device list) (DVB_USB_DIBUSB_MC) [M/n/?] n
      DiBcom DiB0700 USB DVB devices (see help for supported devices) (DVB_USB_DIB0700) [M/n/?] n
      HanfTek UMT-010 DVB-T USB2.0 support (DVB_USB_UMT_010) [M/n/?] n
      Conexant USB2.0 hybrid reference design support (DVB_USB_CXUSB) [M/n/?] n
      Uli m920x DVB-T USB2.0 support (DVB_USB_M920X) [M/n/?] n
      Genesys Logic GL861 USB2.0 support (DVB_USB_GL861) [M/n/?] n
      Alcor Micro AU6610 USB2.0 support (DVB_USB_AU6610) [M/n/?] n
      Nebula Electronics uDigiTV DVB-T USB2.0 support (DVB_USB_DIGITV) [M/n/?] n
      TwinhanDTV Alpha/MagicBoxII, DNTV tinyUSB2, Beetle USB2.0 support (DVB_USB_VP7045) [M/n/?] n
      TwinhanDTV StarBox and clones DVB-S USB2.0 support (DVB_USB_VP702X) [M/n/?] n
      GENPIX 8PSK->USB module support (DVB_USB_GP8PSK) [M/n/?] n
      Hauppauge WinTV-NOVA-T usb2 DVB-T USB2.0 support (DVB_USB_NOVA_T_USB2) [M/n/?] n
      Pinnacle 400e DVB-S USB2.0 support (DVB_USB_TTUSB2) [M/n/?] n
      WideView WT-200U and WT-220U (pen) DVB-T USB2.0 support (Yakumo/Hama/Typhoon/Yuan) (DVB_USB_DTT200U) [M/n/?] m
      Opera1 DVB-S USB2.0 receiver (DVB_USB_OPERA1) [M/n/?] n
      Afatech AF9005 DVB-T USB1.1 support (DVB_USB_AF9005) [M/n/?] n
    Technotrend/Hauppauge Nova-USB devices (DVB_TTUSB_BUDGET) [M/n/?] n
    Technotrend/Hauppauge USB DEC devices (DVB_TTUSB_DEC) [M/n/?] n
    Terratec CinergyT2/qanu USB2 DVB-T receiver (DVB_CINERGYT2) [M/n/?] n
    *
    * Supported FlexCopII (B2C2) Adapters
    *
    Technisat/B2C2 FlexCopII(b) and FlexCopIII adapters (DVB_B2C2_FLEXCOP) [M/n/?] n
    *
    * Supported BT878 Adapters
    *
    *
    * Supported Pluto2 Adapters
    *
    Pluto2 cards (DVB_PLUTO2) [M/n/?] n
    *
    * Supported DVB Frontends
    *
    *
    * Customise DVB Frontends
    *
    Customise the frontend modules to build (DVB_FE_CUSTOMISE) [N/y/?] n
    *
    * DVB-S (satellite) frontends
    *
    ST STV0299 based (DVB_STV0299) [M/n/?] n
    Conexant CX24110 based (DVB_CX24110) [M/n/?] n
    Conexant CX24123 based (DVB_CX24123) [M/n/?] n
    Philips TDA8083 based (DVB_TDA8083) [M/n/?] n
    Zarlink VP310/MT312 based (DVB_MT312) [M/n/?] n
    VLSI VES1893 or VES1993 based (DVB_VES1X93) [M/n/?] n
    Samsung S5H1420 based (DVB_S5H1420) [M/n/?] n
    Philips TDA10086 based (DVB_TDA10086) [M/n/?] n
    *
    * DVB-T (terrestrial) frontends
    *
    Spase sp8870 based (DVB_SP8870) [M/n/?] n
    Spase sp887x based (DVB_SP887X) [M/n/?] n
    Conexant CX22700 based (DVB_CX22700) [M/n/?] n
    Conexant cx22702 demodulator (OFDM) (DVB_CX22702) [M/n/?] n
    LSI L64781 (DVB_L64781) [M/n/?] n
    Philips TDA10045H/TDA10046H based (DVB_TDA1004X) [M/n/?] n
    NxtWave Communications NXT6000 based (DVB_NXT6000) [M/n/?] n
    Zarlink MT352 based (DVB_MT352) [M/n/?] n
    Zarlink ZL10353 based (DVB_ZL10353) [M/n/?] n
    DiBcom 3000M-B (DVB_DIB3000MB) [M/n/?] n
    DiBcom 3000P/M-C (DVB_DIB3000MC) [M/n/?] n
    DiBcom 7000MA/MB/PA/PB/MC (DVB_DIB7000M) [M/n/?] n
    DiBcom 7000PC (DVB_DIB7000P) [M/n/?] n
    *
    * DVB-C (cable) frontends
    *
    VLSI VES1820 based (DVB_VES1820) [M/n/?] n
    Philips TDA10021 based (DVB_TDA10021) [M/n/?] n
    Philips TDA10023 based (DVB_TDA10023) [M/n/?] n
    ST STV0297 based (DVB_STV0297) [M/n/?] n
    *
    * ATSC (North American/Korean Terrestrial/Cable DTV) frontends
    *
    NxtWave Communications NXT2002/NXT2004 based (DVB_NXT200X) [M/n/?] n
    Oren OR51211 based (DVB_OR51211) [M/n/?] n
    Oren OR51132 based (DVB_OR51132) [M/n/?] n
    Broadcom BCM3510 (DVB_BCM3510) [M/n/?] n
    LG Electronics LGDT3302/LGDT3303 based (DVB_LGDT330X) [M/n/?] n
    Samsung S5H1409 based (DVB_S5H1409) [M/n/?] n
    *
    * Tuners/PLL support
    *
    Generic I2C PLL based tuners (DVB_PLL) [M/n/?] n
    Philips TDA826X silicon tuner (DVB_TDA826X) [M/n/?] n
    Philips TDA827X silicon tuner (DVB_TDA827X) [M/n/?] n
    NXP TDA18271 silicon tuner (DVB_TDA18271) [M/n/?] n
    Quantek QT1010 silicon tuner (DVB_TUNER_QT1010) [M/n/?] n
    Microtune MT2060 silicon IF tuner (DVB_TUNER_MT2060) [M/n/?] n
    Microtune MT2266 silicon tuner (DVB_TUNER_MT2266) [M/n/?] n
    Microtune MT2131 silicon tuner (DVB_TUNER_MT2131) [M/n/?] n
    DiBcom DiB0070 silicon base-band tuner (DVB_TUNER_DIB0070) [M/n/?] n
    Xceive XC5000 silicon tuner (DVB_TUNER_XC5000) [M/n/?] n
    *
    * Miscellaneous devices
    *
    LNBP21 SEC controller (DVB_LNBP21) [M/n/?] n
    ISL6421 SEC controller (DVB_ISL6421) [M/n/?] n
    TUA6100 PLL (DVB_TUA6100) [M/n/?] n
DAB adapters (DAB) [Y/n/?] n
*
* Audio devices for multimedia
*
*
* ALSA sound
*
Bt87x Audio Capture (SND_BT87X) [M/n/?] n
*
* OSS sound
*
BT878 audio dma (SOUND_BT878) [M/n/?] n
ACI mixer (miroSOUND PCM1-pro/PCM12/PCM20) (SOUND_ACI_MIXER) [N/m/?] n
TV card (bt848) mixer support (SOUND_TVMIXER) [M/n/?] n
#
# configuration written to .config
#

*** Error during writing of the kernel configuration.

make[1]: *** [config] Error 1
make[1]: Leaving directory `/home/peterm/v4l-dvb/v4l-dvb/v4l'
make: *** [config] Error 2


*****************
Hope this helps
*****************

---

### Post by ugm6hr on 2008-01-19
@madsmadmad:
Thanks for the info, but I have realised I have a different Freecom stick - the revision 4.

Not going to be easy for me: [http://ubuntuforums.org/showthread.php?t=665315](http://ubuntuforums.org/showthread.php?t=665315) :(

---

