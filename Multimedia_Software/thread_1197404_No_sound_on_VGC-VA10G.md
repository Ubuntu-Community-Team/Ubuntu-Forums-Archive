---
title: "No sound on VGC-VA10G"
date: 2009-06-26
forum: Multimedia Software
---

### Post by anova on 2009-06-26
[IMG]http://ecx.images-amazon.com/images/I/41KCN6CRG7L._SL500_AA280_.jpg[/IMG]
Ubuntu 8.10 or 9.04, [sony vaio all-in-one VGC-VA10G]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&productId=11035465")
Sound only in headphones
manipulation with model (vaio or sony or auto) in [Alsa]("http://www.alsa-project.org/") config not working
Sound based on Sigmatel chipset, in system detected  - [Intel HDA]("https://help.ubuntu.com/community/HdaIntelSoundHowto")!

[This answers]("http://www.ubuntuforums.org/showthread.php?t=821353&highlight=VGC-VA10G") not working

help, help where I was wrong!

---

### Post by WJason on 2009-07-02
If you get an answer to this please let me know.  I have the same machine and no sound at all.



Jason
[email]w.jason@toast.net[/email]

---

### Post by zero777zero on 2009-07-02
type "alsamixer" into the terminal and see if you are muted

i used to own two vaios, i ended up switching brands because sony is less than helpful in the driver area with opensource projects

---

### Post by anova on 2009-07-08
> **WJason said:**
> If you get an answer to this please let me know.  I have the same machine and no sound at all.

OK Jason!

> 
type "alsamixer" into the terminal and see if you are muted
i used to own two vaios, i ended up switching brands because sony is less than helpful in the driver area with opensource projects


I have many times type "alsamixer", but there is always On.
sound played only in headphones and very low level.

I can not completely switch to Ubuntu because of sound problem
I have more than 30 times to reinstall and setup Ubuntu 7.04, 8.x, 9x
Support Sony: I have not been able to help, perhaps this VAIO model is intended only for those who WINDOWS liked.

---

### Post by WJason on 2010-07-28
Hi Anova,
I never did find a solution to this problem.  To this day, videos play without sound on my Sony Vaio VGC-VA10G.  On my Acer Netbook, videos don't play at all anymore--at some point I lost sound, then later videos.
I see that 10.4 LTS is released.  I might try that, but I doubt the developers are looking at old hardware anymore.

---

### Post by anova on 2010-07-30
Hi Jason,
I'm on the way to solve this problem by modifying and creating a patch for the selection of the path nodes on the map PinConfigurations.I got the codec but do not have the Data sheet on our map CXD9872RD/K.
We have no one can help, because the party VA10G little spread in the world. I've seen several reports about the installation of Ubuntu 6-7-8-9 and yours 10 in South America and Germany on our series, but there too there was no solution.
Our card has patches in the nucleus, but alas, it just bypassed our extension of cards, this involved a Takashi Iwai it works on Suse [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/) his address tiwai @ suse.de
From the comments to his patch, you can see that the codec loaded before, and he blocked the other profiles.

This codec by my vendor ID 0x83847661, included in [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-emu/hda-emu-0.2.6.tar.bz2](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-emu/hda-emu-0.2.6.tar.bz2) \codecs\stac7661-sony-vaio-fe550g
```
Codec: SigmaTel ID 7661
Address: 0
Vendor Id: 0x83847661
Subsystem Id: 0x104d0c00
Revision Id: 0x104201
Default PCM: rates 0x7e0, bits 0x0e, types 0x1
Default Amp-In caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
Node 0x02 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x03 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x04 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x58 0x58]
  Power: 0x0
Node 0x05 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x06 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x07
Node 0x07 [Audio Selector] wcaps 0x300903: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x0f 0x0f]
  Connection: 1
     0x0e
Node 0x08 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x09
Node 0x09 [Audio Selector] wcaps 0x300903: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x80 0x80]
  Connection: 1
     0x15
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173c: IN OUT HP
  Pin Default 0x03211010: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
  Pin-ctls: 0x00:
  Connection: 1
     0x02
Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0814: OUT
  Pin Default 0x400000fb: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x04
Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0814: OUT
  Pin Default 0x20011011: [Jack] Line Out at Sep N/A
    Conn = 1/8, Color = Black
  Pin-ctls: 0x00:
  Connection: 1
     0x03
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173c: IN OUT HP
  Pin Default 0x41a15020: [N/A] Mic at Ext Rear
    Conn = 1/8, Color = Red
  Pin-ctls: 0x00:
  Connection: 1
     0x02
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x0824: IN
  Pin Default 0x90370060: [Fixed] CD at Int N/A
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0814: OUT
  Pin Default 0xb2010012: [Fixed] Line Out at Oth Front
    Conn = 1/8, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x05
Node 0x10 [Audio Output] wcaps 0x40211: Stereo Digital
  PCM: rates 0x3e0, bits 0x0e, types 0x5
Node 0x11 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x20455040: [Jack] SPDIF Out at Sep N/A
    Conn = Optical, Color = Red
  Pin-ctls: 0x00:
  Connection: 2
     0x10* 0x09
Node 0x12 [Audio Input] wcaps 0x140311: Stereo Digital
  PCM: rates 0x160, bits 0x0e, types 0x5
  Connection: 1
     0x13
Node 0x13 [Pin Complex] wcaps 0x440381: Stereo Digital
  Pincap 0x0834: IN OUT
  Pin Default 0x40c000fd: [N/A] SPDIF In at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x18
Node 0x14 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x90a7002e: [Fixed] Mic at Int N/A
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x00:
Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 4
     0x0a* 0x0d 0x14 0x02
Node 0x16 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=0
  Amp-Out vals:  [0x00]
Node 0x17 [Volume Knob Widget] wcaps 0x600000: Mono
Node 0x18 [Audio Output] wcaps 0x40201: Stereo Digital

```

In this patch included errors for ours card: alsa-kernel\pci\hda\patch_sigmatel.c
PCI soundcards and the code specific to the PCI BUS:
```
STAC9872 hack
 */

static struct hda_verb stac9872_core_init[] = {
	{0x15, AC_VERB_SET_CONNECT_SEL, 0x1}, /* mic-sel: 0a,0d,14,02 */
	{0x15, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_UNMUTE}, /* Mic-in -> 0x9 */
	{}
};

static hda_nid_t stac9872_pin_nids[] = {
	0x0a, 0x0b, 0x0c, 0x0d, 0x0e, 0x0f,
	0x11, 0x13, 0x14,
};

static hda_nid_t stac9872_adc_nids[] = {
	0x8 /*,0x6*/
};

static hda_nid_t stac9872_mux_nids[] = {
	0x15
};

static unsigned long stac9872_capvols[] = {
	HDA_COMPOSE_AMP_VAL(0x09, 3, 0, HDA_INPUT),
};
#define stac9872_capsws		stac9872_capvols

static unsigned int stac9872_vaio_pin_configs[9] = {
	0x03211020, 0x411111f0, 0x411111f0, 0x03a15030,
	0x411111f0, 0x90170110, 0x411111f0, 0x411111f0,
	0x90a7013e
};

static const char *stac9872_models[STAC_9872_MODELS] = {
	[STAC_9872_AUTO] = "auto",
	[STAC_9872_VAIO] = "vaio",
};

static unsigned int *stac9872_brd_tbl[STAC_9872_MODELS] = {
	[STAC_9872_VAIO] = stac9872_vaio_pin_configs,
};

static struct snd_pci_quirk stac9872_cfg_tbl[] = {
	SND_PCI_QUIRK_MASK(0x104d, 0xfff0, 0x81e0,
			   "Sony VAIO F/S", STAC_9872_VAIO),
	{} /* terminator */
};

static int patch_stac9872(struct hda_codec *codec)
{
	struct sigmatel_spec *spec;
	int err;

	spec  = kzalloc(sizeof(*spec), GFP_KERNEL);
	if (spec == NULL)
		return -ENOMEM;
	codec->no_trigger_sense = 1;
	codec->spec = spec;
	spec->num_pins = ARRAY_SIZE(stac9872_pin_nids);
	spec->pin_nids = stac9872_pin_nids;

	spec->board_config = snd_hda_check_board_config(codec, STAC_9872_MODELS,
							stac9872_models,
							stac9872_cfg_tbl);
	if (spec->board_config < 0)
		snd_printdd(KERN_INFO "hda_codec: %s: BIOS auto-probing.\n",
			    codec->chip_name);
	else
		stac92xx_set_config_regs(codec,
					 stac9872_brd_tbl[spec->board_config]);

	spec->multiout.dac_nids = spec->dac_nids;
	spec->num_adcs = ARRAY_SIZE(stac9872_adc_nids);
	spec->adc_nids = stac9872_adc_nids;
	spec->num_muxes = ARRAY_SIZE(stac9872_mux_nids);
	spec->mux_nids = stac9872_mux_nids;
	spec->init = stac9872_core_init;
	spec->num_caps = 1;
	spec->capvols = stac9872_capvols;
	spec->capsws = stac9872_capsws;

	err = stac92xx_parse_auto_config(codec, 0x10, 0x12);
	if (err < 0) {
		stac92xx_free(codec);
		return -EINVAL;
	}
	spec->input_mux = &spec->private_imux;
	codec->patch_ops = stac92xx_patch_ops;
	return 0;
}
```

[Please see 2.2. Codec-Probing Problem]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/docs/HD-Audio.html")
> Thus, if the second error message appears, try to narrow the probed codec slots via probe_mask option. It’s a bitmask, and each bit corresponds to the codec slot. For example, to probe only the first slot, pass probe_mask=1. For the first and the third slots, pass probe_mask=5 (where 5 = 1 | 4), and so on.

Please test "model=test" or "model=generic"


Takashi doc:
> If you are masochistic enough to debug the driver problem, note the following:

[LIST=1]
[*]The speaker (and the headphone, too) output often requires the external amplifier. This can be set usually via EAPD verb or a certain GPIO. If the codec pin supports EAPD, you have a better chance via SET_EAPD_BTL verb (0x70c). On others, GPIO pin (mostly it’s either GPIO0 or GPIO1) may turn on/off EAPD.
[*]Some Realtek codecs require special vendor-specific coefficients to turn on the amplifier. See patch_realtek.c.
[*]IDT codecs may have extra power-enable/disable controls on each analog pin. See patch_sigmatel.c.
[*]Very rare but some devices don’t accept the pin-detection verb until triggered. Issuing GET_PIN_SENSE verb (0xf09) may result in the codec-communication stall. Some examples are found in patch_realtek.c.
[/LIST]

Please use hda-emu and hda-analyzer for more info
[http://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-emu/hda-emu-0.2.6.tar.bz2](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-emu/hda-emu-0.2.6.tar.bz2)
And use par. CONFIG_SND_DEBUG_VERBOSE=y
for get more info about errors
Please post your info from [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)

HDA Analyzer
[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)
```
wget -O run.py http://www.alsa-project.org/hda-analyzer.py
python run.py
python run.py ./alsa-info.txt
python run.py --monitor

```

---

### Post by donut123 on 2011-02-27
Hello...I am wondering if this issue with the Vaio was ever solved?
I have in m y hands this machine..and guess what? The sound wont work..
and I have tried several Distros...is there a current..answer to this problem?

---

### Post by anova on 2011-05-18
> **donut123 said:**
> Hello...I am wondering if this issue with the Vaio was ever solved?
I have in m y hands this machine..and guess what? The sound wont work..
and I have tried several Distros...is there a current..answer to this problem?

NO, and current 11.04 is not work sound.
A very small  count of owners of these computers, and the problem no one could decide, I'm sorry, I spent many hours with installing Ubuntu on this system - no result...

---

