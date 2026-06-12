---
title: "No sound in Kubuntu 14.04"
date: 2014-10-15
forum: Multimedia Software
---

### Post by Adrian_Ber on 2014-10-15
I have an HP EliteBook 8560w with Kubuntu 14.04 and 3.13.0-30 kernel.

Sound is not working. I tried to 

 - upgrade the system
 - reinstall pulseaudio
 - add ```
options snd-hda-intel model=auto
``` (also tried with ```
model=hp
```) to ```
/etc/modprobe.d/alsa-base.conf
```

At boot time I get the following errors:

```
    genirq: Flags mismatch irq 5. 00000080 (snd_hda_intel) vs. 00000000 (parport0)
    hda-intel: unable to grab IRQ 5, disabling device
```


Output of `aplay -l` is

```
     List of PLAYBACK Hardware Devices ****
    card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0

```
In `alsamixer` the channels are 0 and cannot be modified.

Output of `lsmod` is

```
    Module                  Size  Used by
    ppp_deflate            12950  0 
    bsd_comp               12921  0 
    ppp_async              17413  1 
    crc_ccitt              12707  1 ppp_async
    huawei_cdc_ncm         12966  0 
    cdc_wdm                19053  1 huawei_cdc_ncm
    cdc_ncm                24511  1 huawei_cdc_ncm
    usbnet                 43913  2 huawei_cdc_ncm,cdc_ncm
    mii                    13934  1 usbnet
    option                 42468  2 
    usb_wwan               20429  1 option
    usbserial              45014  7 option,usb_wwan
    usb_storage            62209  0 
    ctr                    13049  0 
    ccm                    17773  0 
    nvram                  14411  0 
    rfcomm                 69160  8 
    bnep                   19624  2 
    binfmt_misc            17468  1 
    btusb                  32412  0 
    bluetooth             395423  22 bnep,btusb,rfcomm
    hp_wmi                 14062  0 
    sparse_keymap          13948  1 hp_wmi
    mxm_wmi                13021  0 
    snd_hda_codec_hdmi     46207  4 
    intel_rapl             18773  0 
    x86_pkg_temp_thermal    14205  0 
    intel_powerclamp       14705  0 
    coretemp               13435  0 
    kvm                   451511  0 
    crct10dif_pclmul       14289  0 
    crc32_pclmul           13113  0 
    ghash_clmulni_intel    13216  0 
    aesni_intel            55624  0 
    aes_x86_64             17131  1 aesni_intel
    lrw                    13286  1 aesni_intel
    gf128mul               14951  1 lrw
    glue_helper            13990  1 aesni_intel
    ablk_helper            13597  1 aesni_intel                                                                                                                                                                                                                                    
    cryptd                 20359  3    ghash_clmulni_intel,aesni_intel,ablk_helper                                                                                                                                                                                                    
    snd_hda_intel          52355  4                                                                                                                                                                                                                                                
    arc4                   12608  2                                                                                                                                                                                                                                                
    snd_hda_codec         192906  2 snd_hda_codec_hdmi,snd_hda_intel                                                                                                                                                                                                               
    snd_hwdep              13602  1 snd_hda_codec                                                                                                                                                                                                                                  
    iwldvm                232285  0                                                                                                                                                                                                                                                
    mac80211              626557  1 iwldvm                                                                                                                                                                                                                                         
    snd_pcm               102099  3    snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel                                                                                                                                                                                                 
    snd_page_alloc         18710  2 snd_pcm,snd_hda_intel                                                                                                                                                                                                                          
    snd_seq_midi           13324  0                                                                                                                                                                                                                                                
    snd_seq_midi_event     14899  1 snd_seq_midi                                                                                                                                                                                                                                   
    snd_rawmidi            30144  1 snd_seq_midi                                                                                                                                                                                                                                   
    snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi                                                                                                                                                                                                                
    snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi                                                                                                                                                                                                               
    joydev                 17381  0                                                                                                                                                                                                                                                
    snd_timer              29482  2 snd_pcm,snd_seq                                                                                                                                                                                                                                
    serio_raw              13462  0                                                                                                                                                                                                                                                
    iwlwifi               169932  1 iwldvm                                                                                                                                                                                                                                         
    nvidia              10675249  51                                                                                                                                                                                                                                               
    snd                    69238  18 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi                                                                                                                    
    cfg80211              484040  3 iwlwifi,mac80211,iwldvm                                                                                                                                                                                                                        
    lpc_ich                21080  0                                                                                                                                                                                                                                                
    drm                   303102  2 nvidia                                                                                                                                                                                                                                         
    soundcore              12680  1 snd
    mei_me                 18627  0 
    tpm_infineon           17372  0 
    hp_accel               26012  0 
    wmi                    19177  2 hp_wmi,mxm_wmi
    mei                    82276  1 mei_me
    lis3lv02d              20156  1 hp_accel
    input_polldev          13896  1 lis3lv02d
    mac_hid                13205  0 
    parport_pc             32701  1 
    ppdev                  17671  0 
    lp                     17759  0 
    parport                42348  3 lp,ppdev,parport_pc
    psmouse               102222  0 
    ahci                   25819  3 
    libahci                32168  1 ahci
    firewire_ohci          40409  0 
    sdhci_pci              23172  0 
    sdhci                  43015  1 sdhci_pci
    firewire_core          68769  1 firewire_ohci
    crc_itu_t              12707  1 firewire_core
    e1000e                254433  0 
    video                  19476  0 
    ptp                    18933  1 e1000e
    pps_core               19382  1 ptp

```

There is no hardware problem, the sound works fine in Windows.
Any idea?

---

### Post by SeijiSensei on 2014-10-15
I install **plasma-widget-veromix** to replace the volume control applet in Kubuntu.  It lets you switch easily among the various available audio options.  Are you trying to get audio from the HDMI port?

---

