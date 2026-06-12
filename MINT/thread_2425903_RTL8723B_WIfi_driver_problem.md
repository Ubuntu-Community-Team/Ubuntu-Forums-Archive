---
title: "RTL8723B WIfi driver problem"
date: 2019-09-01
forum: MINT
---

### Post by fraizor on 2019-09-01
Hello everyone

i am facing a weird wifi problem 

i have low end laptop Chinese "Zed Air 2" RTL8723B

running Linux mint 19 based on [B]Ubuntu 18.04

[/B]the wifi was running perfectly on stock windows 10 [B](photo atttached)
[/B]
on linux mint direclty after instullation it does see wifi networks sometimes and sometimes it does not see any
when it does see wifi networks i cant connectat all.

i tried couple of posts but with no luck 

this is the last thing i tried [https://ubuntuforums.org/showthread.php?t=2333979](https://ubuntuforums.org/showthread.php?t=2333979) i did exactly as MR**[COLOR=#DD4814][B] chili555**[/COLOR][/B]  	 suggested[URL="https://ubuntuforums.org/showthread.php?t=2333979"]
[/URL]
after couple of reboots i can successfully connect to my network but after another reboot it wont see wifi networks any more

```
user@user-pc:~$ dmesg | grep -i rtl
[    7.343296] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    7.343300] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[    7.349156] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[    7.349163] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[    7.546818] usb 1-7: rtl8723bu_parse_efuse: dumping efuse (0x200 bytes):
[    7.546923] usb 1-7: RTL8723BU rev E (SMIC) 1T1R, TX queues 3, WiFi=1, BT=1, GPS=0, HI PA=0
[    7.546925] usb 1-7: RTL8723BU MAC: 54:c9:df:43:cf:8b
[    7.546928] usb 1-7: rtl8xxxu: Loading firmware rtlwifi/rtl8723bu_nic.bin
[    8.338913] usbcore: registered new interface driver rtl8xxxu
[    8.499026] RTL871X: module init start
[    8.499032] RTL871X: rtl8723bu v4.3.6.11_12942.20141204_BTCOEX20140507-4E40
[    8.499033] RTL871X: rtl8723bu BT-Coex version = BTCOEX20140507-4E40
[    8.499116] usbcore: registered new interface driver rtl8723bu
[    8.499117] RTL871X: module init ret=0
[   11.311774] rtl8xxxu 1-7:1.2 wlx54c9df43cf8b: renamed from wlan0


```

any help is highly appreciated

[ATTACH=CONFIG]283913[/ATTACH]

---

### Post by coffeecat on 2019-09-01
*Thread moved to Mint sub-forum.*

---

### Post by jeremy31 on 2019-09-01
Update the kernel to at least 4.15.0-54 and do
```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot

---

### Post by fraizor on 2019-09-01
thanks for fast replay 

i am already running 4.15.0-54

> $ uname -r
4.15.0-54-generic




> echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be.conf
options rtl8723be ant_sel=2




i did that then rebooted still the same problem :(

---

### Post by chili555 on 2019-09-02
May we see:```
lsusb
lsmod
```

---

### Post by jeremy31 on 2019-09-02
Hi chili555, wireless script results [https://termbin.com/on4f](https://termbin.com/on4f)

---

### Post by chili555 on 2019-09-04
We're not sure what we are seeing here. Are we seeing the results of the working USB adapter or the not-working-sometimes adapter. Please remove the adapter that you suspect is working fine and reboot. Next, run and post the wireless script again.

---

### Post by fraizor on 2019-09-05
hello

i ran the following with no external wifi dongle attached

```
user@user-pc:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 1908:2311 GEMBIRD 
Bus 001 Device 004: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@user-pc:~$ lsmod
Module                  Size  Used by
rfcomm                 77824  16
ccm                    20480  0
joydev                 24576  0
spi_pxa2xx_platform    24576  0
8250_dw                16384  0
hid_multitouch         20480  0
bnep                   20480  2
intel_rapl             20480  0
intel_telemetry_pltdrv    20480  0
intel_punit_ipc        16384  1 intel_telemetry_pltdrv
intel_telemetry_core    16384  1 intel_telemetry_pltdrv
intel_pmc_ipc          20480  1 intel_telemetry_pltdrv
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           188416  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
nls_iso8859_1          16384  1
intel_rapl_perf        16384  0
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
input_leds             16384  0
serio_raw              16384  0
lpc_ich                24576  0
snd_soc_skl            90112  0
snd_soc_skl_ipc        65536  1 snd_soc_skl
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_acpi           16384  1 snd_soc_skl
snd_soc_core          241664  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
8723bu                897024  0
arc4                   16384  2
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
media                  40960  2 videodev,uvcvideo
rtl8xxxu              122880  0
rtsx_usb_ms            20480  0
mac80211              778240  1 rtl8xxxu
memstick               16384  1 rtsx_usb_ms
btusb                  45056  0
r8188eu               421888  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             548864  43 btrtl,btintel,btbcm,bnep,btusb,rfcomm
snd_hda_intel          40960  3
ecdh_generic           24576  1 bluetooth
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  7 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_soc_skl
cfg80211              622592  3 mac80211,8723bu,r8188eu
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  8 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_soc_core,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
idma64                 20480  6
mei_me                 40960  0
virt_dma               16384  1 idma64
intel_lpss_pci         20480  0
intel_lpss             16384  1 intel_lpss_pci
mei                    90112  1 mei_me
snd                    81920  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
processor_thermal_device    16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
soundcore              16384  1 snd
mac_hid                16384  0
intel_hid              16384  0
int3400_thermal        16384  0
sparse_keymap          16384  1 intel_hid
int3403_thermal        16384  0
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
acpi_thermal_rel       16384  1 int3400_thermal
dptf_power             16384  0
int3406_thermal        16384  0
sch_fq_codel           20480  5
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
btrfs                1122304  0
xor                    24576  1 btrfs
zstd_compress         163840  1 btrfs
raid6_pq              114688  1 btrfs
dm_mirror              24576  0
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
rtsx_usb_sdmmc         28672  0
rtsx_usb               20480  2 rtsx_usb_sdmmc,rtsx_usb_ms
mmc_block              36864  3
i915                 1617920  15
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
psmouse               147456  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
i2c_hid                20480  0
fb_sys_fops            16384  1 drm_kms_helper
ahci                   40960  0
drm                   401408  6 drm_kms_helper,i915
libahci                32768  1 ahci
sdhci_pci              32768  0
hid                   118784  2 i2c_hid,hid_multitouch
sdhci                  49152  1 sdhci_pci
video                  45056  2 int3406_thermal,i915
pinctrl_broxton        40960  3


```

---

### Post by coffeecat on 2019-09-05
@fraizor, I've changed the BBCode quote tags to code tags for your terminal output in order to restore columnar formatting. Please use code tags, not quote tags, for terminal output and for posting the contents of config files. There's a link in my sig if you need it.

Also, please re-read chili555's last post.

---

### Post by fraizor on 2019-09-05
hello

please find attached script output when wifi doungle not attached[ATTACH]283938[/ATTACH]


sorry forgot to reboot
here is the output after reboot with no doungle
[ATTACH]283939[/ATTACH]

---

### Post by chili555 on 2019-09-05
First, you have two possibly conflicting drivers loaded. Let's remove one and see if connectivity improves:

```
sudo -i
modprobe -r rtl8xxxu
echo "blacklist rtl8xxxu"  >>  /etc/modprobe.d/blacklist.conf
exit
```Also, we see:

> Cell 01 - Address: <MAC 'Amerat' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Amerat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003f44329180
                    Extra: Last beacon: 1004ms ago
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

After making these changes, is there any improvement in connectivity?

---

### Post by fraizor on 2019-09-05
hello

thank you very much 
yes indeed it was a conflicted drivers 

i ran the first code box you wrote then rebooted now wifi is working 100%
i  am writing this comment using the internal wifi card
one small issue that i can see 2 adapters in the wifi manager although i dont have any attached wifi dongle currently 

how can i remove the fake wifi ?

[ATTACH=CONFIG]283941[/ATTACH]

---

### Post by chili555 on 2019-09-05
I assume that you still have the files for the driver you compiled. Does the Makefile mention concurrent mode?```
cd rtl8723bu  <--*or wherever the file is located*
cat Makefile | grep -i concurrent
```Did you install the driver with dkms?```
sudo dkms status
```

---

### Post by fraizor on 2019-09-05
user@user-pc:~$ cd rtl8723bu
user@user-pc:~/rtl8723bu$ cat Makefile | grep -i concurrent
EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE
user@user-pc:~/rtl8723bu$ sudo dkms status
[sudo] password for user:    

assume that you still have the files for the driver you compiled. Does the Makefile mention concurrent mode?
yup

Did you install the driver with dkms?
i have no idea, running 
sudo dkms status 

does not return anything 

i only did what you suggested here 



[https://ubuntuforums.org/showthread.php?t=2333979](https://ubuntuforums.org/showthread.php?t=2333979)

---

### Post by chili555 on 2019-09-05
> 
EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE
Please find that line in the Makefile:```
nano Makefile
```Place a # at the beginning so that it now reads:

```
**#**EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE
```Save the change, Ctrl+o followed by Enter and exit the text editor, Ctrl+x.

Now recompile:```
sudo make uninstall
make clean
make
sudo make install
```Reboot.

---

### Post by fraizor on 2019-09-05
et voilà !

everything is now perfect you are my hero thank you chili555 8-)

---

### Post by chili555 on 2019-09-05
Glad it's working as expected. Please use thread tools at the top to mark Solved.

---

