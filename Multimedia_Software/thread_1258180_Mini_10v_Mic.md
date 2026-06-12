---
title: "Mini 10v Mic"
date: 2009-09-04
forum: Multimedia Software
---

### Post by vahnx on 2009-09-04
I've went through 5 pages of Google and all the search results on how to get the mic working on a Dell Mini 10v in Ubuntu 9.04 netbook remix and the closest I came, I found this patch:

[I]diff --git a/sound/pci/hda/patch_realtek.c b/sound/pci/hda/patch_realtek.c
index a4422e5..db91cf8 100644
--- a/sound/pci/hda/patch_realtek.c
+++ b/sound/pci/hda/patch_realtek.c
@@ -183,6 +183,7 @@ enum {
    ALC663_ASUS_MODE4,
    ALC663_ASUS_MODE5,
    ALC663_ASUS_MODE6,
+    ALC272_DELL_ZM1,
    ALC662_AUTO,
    ALC662_MODEL_LAST,
};
@@ -14687,6 +14688,10 @@ static hda_nid_t alc662_dac_nids[4] = {
    0x02, 0x03, 0x04
};

+static hda_nid_t alc272_dac_nids[2] = {
+ 0x02, 0x03
+};
+
static hda_nid_t alc662_adc_nids[1] = {
    /* ADC1-2 */
    0x09,
@@ -15328,6 +15333,22 @@ static struct hda_verb alc662_ecs_init_verbs[] = {
    {}
};

+static struct hda_verb alc272_dell_zm1_init_verbs[] = {
+ {0x12, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_IN},
+ {0x13, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_IN},
+ {0x15, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_IN},
+ {0x16, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_IN},
+ {0x21, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_HP},
+ {0x21, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_UNMUTE},
+ {0x21, AC_VERB_SET_CONNECT_SEL, 0x01}, /* Headphone */
+ {0x22, AC_VERB_SET_AMP_GAIN_MUTE, AMP_IN_MUTE(0)},
+ {0x22, AC_VERB_SET_AMP_GAIN_MUTE, AMP_IN_UNMUTE(9)},
+ {0x18, AC_VERB_SET_UNSOLICITED_ENABLE, AC_USRSP_EN | ALC880_MIC_EVENT},
+ {0x21, AC_VERB_SET_UNSOLICITED_ENABLE, AC_USRSP_EN | ALC880_HP_EVENT},
+ {}
+};
+
+
/* capture mixer elements */
static struct snd_kcontrol_new alc662_capture_mixer[] = {
    HDA_CODEC_VOLUME("Capture Volume", 0x09, 0x0, HDA_INPUT),
@@ -15353,6 +15374,7 @@ static struct snd_kcontrol_new alc662_auto_capture_mixer[] = {
    { } /* end */
};

+
static void alc662_lenovo_101e_ispeaker_automute(struct hda_codec *codec)
{
    unsigned int present;
@@ -15849,6 +15871,7 @@ static const char *alc662_models[ALC662_MODEL_LAST] = {
    [ALC662_ASUS_EEEPC_P701] = "eeepc-p701",
    [ALC662_ASUS_EEEPC_EP20] = "eeepc-ep20",
    [ALC662_ECS] = "ecs",
+    [ALC272_DELL_ZM1] = "dell-zm1",
    [ALC663_ASUS_M51VA] = "m51va",
    [ALC663_ASUS_G71V] = "g71v",
    [ALC663_ASUS_H13] = "h13",
@@ -15905,6 +15928,7 @@ static struct snd_pci_quirk alc662_cfg_tbl[] = {
    SND_PCI_QUIRK(0x17aa, 0x101e, "Lenovo", ALC662_LENOVO_101E),
    SND_PCI_QUIRK(0x1019, 0x9087, "ECS", ALC662_ECS),
    SND_PCI_QUIRK(0x105b, 0x0cd6, "Foxconn", ALC662_ECS),
+    SND_PCI_QUIRK(0x1028, 0x02f4, "DELL ZM1", ALC272_DELL_ZM1),
    SND_PCI_QUIRK(0x1458, 0xa002, "Gigabyte 945GCM-S2L",
         ALC662_3ST_6ch_DIG),
    SND_PCI_QUIRK(0x1565, 0x820f, "Biostar TA780G M2+", ALC662_3ST_6ch_DIG),
@@ -16012,6 +16036,20 @@ static struct alc_config_preset alc662_presets[] = {
        .unsol_event = alc662_eeepc_unsol_event,
        .init_hook = alc662_eeepc_inithook,
    },
+ [ALC272_DELL_ZM1] = {
+ .mixers = { alc663_m51va_mixer, alc662_auto_capture_mixer },
+ .init_verbs = { alc662_init_verbs, alc272_dell_zm1_init_verbs },
+ .num_dacs = ARRAY_SIZE(alc272_dac_nids),
+ .dac_nids = alc662_dac_nids,
+ .num_channel_mode = ARRAY_SIZE(alc662_3ST_2ch_modes),
+ .adc_nids = alc662_adc_nids,
+ .num_adc_nids = ARRAY_SIZE(alc662_adc_nids),
+ .capsrc_nids = alc662_capsrc_nids,
+ .channel_mode = alc662_3ST_2ch_modes,
+ .input_mux = &alc663_m51va_capture_source,
+ .unsol_event = alc663_m51va_unsol_event,
+ .init_hook = alc663_m51va_inithook,
+ },
    [ALC663_ASUS_M51VA] = {
        .mixers = { alc663_m51va_mixer, alc662_capture_mixer},
        .init_verbs = { alc662_init_verbs, alc663_m51va_init_verbs },

-- 
1.6.0.4
[/I]

I saved it into a file in **/usr/src** and ran **patch -p1 < micpatch** on it and it prompted me with:

[I]can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/sound/pci/hda/patch_realtek.c b/sound/pci/hda/patch_realtek.c
|index a4422e5..db91cf8 100644
|--- a/sound/pci/hda/patch_realtek.c
|+++ b/sound/pci/hda/patch_realtek.c
--------------------------
File to patch: 
[/I]

From here I am stumped. I believe I may have did something wrong as I found no clear newbie instructions on how to apply the above patch. If anyone has a definitive answer to solving the Mini 10v mic problem, please feel free to post it. I know upgrading to Karmic will fix it but I heard it's unstable and I prefer 9.04 for the time being.

My system is freshly formatted with little-to-no apps installed, along with all the updates.

Thanks in advance.

---

