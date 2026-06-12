---
title: "ENLTV-FM Remote"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by truptrup on 2007-02-21
Has anyone gotten the enltvfm remote working in lirc or at all. I got the tuner and svideo in working with card=3,tuner2 but i cant seem to get the remote to work at all.

---

### Post by cpaulin on 2007-03-07
I have been trying to get the remote to work as well. Everything else about the cards is functioning and setup with mythtv

I found this patch elsewhere on the net but being a linux novice I have no idea how to install it... Anyone understand how to do this and have reasonable instructions on installation? I do not get any response when I cat /dev/input/event2 which is where my ir card shows up under /proc/bus/input/devices. I had read how to cat the output of another low level function but cannot remember where it was to do it again. However, it did show unidentified key down and up when I pressed the remote, so I know it is functional on some level. Can I install the patch below or pullout some of the key defs to make a lirc config file? Any help would be so greatly appreciated. Anyway here is the patch, THANKS!:


lists-archives.org

Mailing Lists Archives
[PATCH] Encore ENLTV-FM

    * Date: Fri, 22 Dec 2006 12:32:58 -0300
    * From: sorman <sorman@xxxxxxxxx>
    * Subject: [PATCH] Encore ENLTV-FM

updated patch against latest master:

Signed-off-by: Juan Pablo Sormani <sorman@xxxxxxxxx>

diff -r d271c9d20d45 linux/Documentation/video4linux/CARDLIST.saa7134
--- a/linux/Documentation/video4linux/CARDLIST.saa7134	Thu Dec 21
17:07:08 2006 -0200
+++ b/linux/Documentation/video4linux/CARDLIST.saa7134	Wed Dec 20
11:18:59 2006 -0300
@@ -104,4 +104,5 @@ 103 -> Compro Videomate DVB-T200A
103 -> Compro Videomate DVB-T200A
104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     [0070:6701]
105 -> Terratec Cinergy HT PCMCIA               [153b:1172]
-106 -> Encore ENLTV                             [1131:2342]
+106 -> Encore ENLTV                             [1131:2341,1131:2342,3016:2344]
+107 -> Encore ENLTV-FM                          [1131:230f]
diff -r d271c9d20d45 linux/drivers/media/common/ir-keymaps.c
--- a/linux/drivers/media/common/ir-keymaps.c	Thu Dec 21 17:07:08 2006 -0200
+++ b/linux/drivers/media/common/ir-keymaps.c	Wed Dec 20 10:07:33 2006 -0300
@@ -1704,3 +1704,88 @@ IR_KEYTAB_TYPE ir_codes_asus_pc39[IR_KEY
};

EXPORT_SYMBOL_GPL(ir_codes_asus_pc39);
+
+
+/* Encore ENLTV-FM  - black plastic, white front cover with white
glowing buttons
+    Juan Pablo Sormani <sorman@xxxxxxxxx> */
+IR_KEYTAB_TYPE ir_codes_encore_enltv[IR_KEYTAB_SIZE] = {
+
+	/* Power button does nothing, neither in Windows app,
+	 although it sends data (used for BIOS wakeup?) */
+	[ 0x0d ] = KEY_MUTE,
+
+	[ 0x1e ] = KEY_TV,
+	[ 0x00 ] = KEY_VIDEO,
+	[ 0x01 ] = KEY_AUDIO,		/* music */
+	[ 0x02 ] = KEY_MHP,		/* picture */
+
+	[ 0x1f ] = KEY_1,
+	[ 0x03 ] = KEY_2,
+	[ 0x04 ] = KEY_3,
+	[ 0x05 ] = KEY_4,
+	[ 0x1c ] = KEY_5,
+	[ 0x06 ] = KEY_6,
+	[ 0x07 ] = KEY_7,
+	[ 0x08 ] = KEY_8,
+	[ 0x1d ] = KEY_9,
+	[ 0x0a ] = KEY_0,
+	
+	[ 0x09 ] = KEY_LIST,        /* -/-- */
+	[ 0x0b ] = KEY_LAST,        /* recall */
+
+	[ 0x14 ] = KEY_HOME,		/* win start menu */
+	[ 0x15 ] = KEY_EXIT,		/* exit */
+#if 0
+	[ 0x16 ] = KEY_CHANNELUP,	/* UP */
+	[ 0x12 ] = KEY_CHANNELDOWN,	/* DOWN */
+	[ 0x0c ] = KEY_VOLUMEUP,	/* RIGHT */
+	[ 0x17 ] = KEY_VOLUMEDOWN,	/* LEFT */
+#else
+	[ 0x16 ] = KEY_UP,
+	[ 0x12 ] = KEY_DOWN,
+	[ 0x0c ] = KEY_RIGHT,
+	[ 0x17 ] = KEY_LEFT,
+#endif
+
+	[ 0x18 ] = KEY_ENTER,		/* OK */
+
+	[ 0x0e ] = KEY_ESC,
+	[ 0x13 ] = KEY_D,		/* desktop */
+	[ 0x11 ] = KEY_TAB,
+	[ 0x19 ] = KEY_SWITCHVIDEOMODE,	/* switch */
+	
+	[ 0x1a ] = KEY_MENU,
+	[ 0x1b ] = KEY_ZOOM,		/* fullscreen */
+	[ 0x44 ] = KEY_TIME,		/* time shift */
+	[ 0x40 ] = KEY_MODE,		/* source */
+
+	[ 0x5a ] = KEY_RECORD,
+	[ 0x42 ] = KEY_PLAY,		/* play/pause */
+	[ 0x45 ] = KEY_STOP,
+	[ 0x43 ] = KEY_CAMERA,		/* camera icon */
+
+	[ 0x48 ] = KEY_REWIND,
+	[ 0x4a ] = KEY_FASTFORWARD,
+	[ 0x49 ] = KEY_PREVIOUS,
+	[ 0x4b ] = KEY_NEXT,
+
+	[ 0x4c ] = KEY_FAVORITES,	/* tv wall */
+	[ 0x4d ] = KEY_SOUND,		/* DVD sound */
+	[ 0x4e ] = KEY_LANGUAGE,	/* DVD lang */
+	[ 0x4f ] = KEY_TEXT,		/* DVD text */
+
+	[ 0x50 ] = KEY_SLEEP,		/* shutdown */
+	[ 0x51 ] = KEY_MODE,		/* stereo > main */
+	[ 0x52 ] = KEY_SELECT,		/* stereo > sap */
+	[ 0x53 ] = KEY_PROG1,		/* teletext */
+
+
+	[ 0x59 ] = KEY_RED,		/* AP1 */
+	[ 0x41 ] = KEY_GREEN,		/* AP2 */
+	[ 0x47 ] = KEY_YELLOW,		/* AP3 */
+	[ 0x57 ] = KEY_BLUE,		/* AP4 */
+
+
+};
+
+EXPORT_SYMBOL_GPL(ir_codes_encore_enltv);
diff -r d271c9d20d45 linux/drivers/media/video/saa7134/saa7134-cards.c
--- a/linux/drivers/media/video/saa7134/saa7134-cards.c	Thu Dec 21
17:07:08 2006 -0200
+++ b/linux/drivers/media/video/saa7134/saa7134-cards.c	Wed Dec 20
11:53:06 2006 -0300
@@ -3223,8 +3223,10 @@ struct saa7134_board saa7134_boards[] =
		}},
	},
	[SAA7134_BOARD_ENCORE_ENLTV] = {
-		/* Steven Walter <stevenrwalter@xxxxxxxxx> */
+	/* Steven Walter <stevenrwalter@xxxxxxxxx>
+	   Juan Pablo Sormani <sorman@xxxxxxxxx> */
		.name           = "Encore ENLTV",
+		.audio_clock    = 0x00200000,
		.tuner_type     = TUNER_TNF_5335MF,
		.radio_type     = UNSET,
		.tuner_addr	= ADDR_UNSET,
@@ -3232,13 +3234,71 @@ struct saa7134_board saa7134_boards[] =
		.inputs         = {{
			.name = name_tv,
			.vmux = 1,
-			.amux = LINE2,
-			.tv   = 1,
-		},{
-			.name = name_svideo,
-			.vmux = 6,
-			.amux = LINE1,
-		}},
+			.amux = 3,
+			.tv   = 1,
+		},{
+			.name = name_tv_mono,
+			.vmux = 7,
+			.amux = 4,
+			.tv   = 1,
+		},{
+			.name = name_comp1,
+			.vmux = 3,
+			.amux = 2,
+		},{
+			.name = name_svideo,
+			.vmux = 0,
+			.amux = 2,
+		}},
+		.radio = {
+			.name = name_radio,
+			.amux = LINE2,
+/*			.gpio = 0x00300001,*/
+			.gpio = 0x20000,
+
+		},
+		.mute = {
+			.name = name_mute,
+			.amux = 0,
+		},
+	},
+	[SAA7134_BOARD_ENCORE_ENLTV_FM] = {
+  /*	Juan Pablo Sormani <sorman@xxxxxxxxx> */
+		.name           = "Encore ENLTV-FM",
+		.audio_clock    = 0x00200000,
+		.tuner_type     = TUNER_PHILIPS_ATSC,
+		.radio_type     = UNSET,
+		.tuner_addr	= ADDR_UNSET,
+		.radio_addr	= ADDR_UNSET,
+		.inputs         = {{
+			.name = name_tv,
+			.vmux = 1,
+			.amux = 3,
+			.tv   = 1,
+		},{
+			.name = name_tv_mono,
+			.vmux = 7,
+			.amux = 4,
+			.tv   = 1,
+		},{
+			.name = name_comp1,
+			.vmux = 3,
+			.amux = 2,
+		},{
+			.name = name_svideo,
+			.vmux = 0,
+			.amux = 2,
+		}},
+		.radio = {
+			.name = name_radio,
+			.amux = LINE2,
+			.gpio = 0x20000,
+
+		},
+		.mute = {
+			.name = name_mute,
+			.amux = 0,
+		},
	},
};

@@ -3884,6 +3944,24 @@ struct pci_device_id saa7134_pci_tbl[] =
		.subvendor    = PCI_VENDOR_ID_PHILIPS,
		.subdevice    = 0x2342,
		.driver_data  = SAA7134_BOARD_ENCORE_ENLTV,
+	},{
+		.vendor       = PCI_VENDOR_ID_PHILIPS,
+		.device       = PCI_DEVICE_ID_PHILIPS_SAA7130,
+		.subvendor    = 0x1131,
+		.subdevice    = 0x2341,
+		.driver_data  = SAA7134_BOARD_ENCORE_ENLTV,
+	},{
+		.vendor       = PCI_VENDOR_ID_PHILIPS,
+		.device       = PCI_DEVICE_ID_PHILIPS_SAA7130,
+		.subvendor    = 0x3016,
+		.subdevice    = 0x2344,
+		.driver_data  = SAA7134_BOARD_ENCORE_ENLTV,
+	},{
+		.vendor       = PCI_VENDOR_ID_PHILIPS,
+		.device       = PCI_DEVICE_ID_PHILIPS_SAA7130,
+		.subvendor    = 0x1131,
+		.subdevice    = 0x230f,
+		.driver_data  = SAA7134_BOARD_ENCORE_ENLTV_FM,
	},{
		/* --- boards without eeprom + subsystem ID --- */
		.vendor       = PCI_VENDOR_ID_PHILIPS,
@@ -4030,6 +4108,8 @@ int saa7134_board_init1(struct saa7134_d
	case SAA7134_BOARD_FLYDVBTDUO:
	case SAA7134_BOARD_PROTEUS_2309:
	case SAA7134_BOARD_AVERMEDIA_A16AR:
+	case SAA7134_BOARD_ENCORE_ENLTV:
+	case SAA7134_BOARD_ENCORE_ENLTV_FM:
		dev->has_remote = SAA7134_REMOTE_GPIO;
		break;
	case SAA7134_BOARD_FLYDVBS_LR300:
diff -r d271c9d20d45 linux/drivers/media/video/saa7134/saa7134-input.c
--- a/linux/drivers/media/video/saa7134/saa7134-input.c	Thu Dec 21
17:07:08 2006 -0200
+++ b/linux/drivers/media/video/saa7134/saa7134-input.c	Wed Dec 20
11:16:19 2006 -0300
@@ -327,6 +327,13 @@ int saa7134_input_init1(struct saa7134_d
		mask_keydown = 0x0040000;
		rc5_gpio = 1;
		break;
+	case SAA7134_BOARD_ENCORE_ENLTV:
+	case SAA7134_BOARD_ENCORE_ENLTV_FM:
+		ir_codes     = ir_codes_encore_enltv;
+		mask_keycode = 0x00007f;
+		mask_keyup   = 0x040000;
+		polling      = 50; // ms
+		break;
	}
	if (NULL == ir_codes) {
		printk("%s: Oops: IR config error [card=%d]\n",
diff -r d271c9d20d45 linux/drivers/media/video/saa7134/saa7134.h
--- a/linux/drivers/media/video/saa7134/saa7134.h	Thu Dec 21 17:07:08 2006 -0200
+++ b/linux/drivers/media/video/saa7134/saa7134.h	Wed Dec 20 11:15:25 2006 -0300
@@ -242,6 +242,7 @@ struct saa7134_format {
#define SAA7134_BOARD_HAUPPAUGE_HVR1110    104
#define SAA7134_BOARD_CINERGY_HT_PCMCIA    105
#define SAA7134_BOARD_ENCORE_ENLTV         106
+#define SAA7134_BOARD_ENCORE_ENLTV_FM      107

#define SAA7134_MAXBOARDS 8
#define SAA7134_INPUT_MAX 8
diff -r d271c9d20d45 linux/include/media/ir-common.h
--- a/linux/include/media/ir-common.h	Thu Dec 21 17:07:08 2006 -0200
+++ b/linux/include/media/ir-common.h	Fri Dec 22 12:25:53 2006 -0300
@@ -141,6 +141,7 @@ extern IR_KEYTAB_TYPE ir_codes_proteus_2
extern IR_KEYTAB_TYPE ir_codes_proteus_2309[IR_KEYTAB_SIZE];
extern IR_KEYTAB_TYPE ir_codes_budget_ci_old[IR_KEYTAB_SIZE];
extern IR_KEYTAB_TYPE ir_codes_asus_pc39[IR_KEYTAB_SIZE];
+extern IR_KEYTAB_TYPE ir_codes_encore_enltv[IR_KEYTAB_SIZE];

#endif

diff -r d271c9d20d45 linux/Documentation/video4linux/CARDLIST.saa7134
--- a/linux/Documentation/video4linux/CARDLIST.saa7134	Thu Dec 21 17:07:08 2006 -0200
+++ b/linux/Documentation/video4linux/CARDLIST.saa7134	Wed Dec 20 11:18:59 2006 -0300
@@ -104,4 +104,5 @@ 103 -> Compro Videomate DVB-T200A
 103 -> Compro Videomate DVB-T200A
 104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     [0070:6701]
 105 -> Terratec Cinergy HT PCMCIA               [153b:1172]
-106 -> Encore ENLTV                             [1131:2342]
+106 -> Encore ENLTV                             [1131:2341,1131:2342,3016:2344]
+107 -> Encore ENLTV-FM                          [1131:230f]
diff -r d271c9d20d45 linux/drivers/media/common/ir-keymaps.c
--- a/linux/drivers/media/common/ir-keymaps.c	Thu Dec 21 17:07:08 2006 -0200
+++ b/linux/drivers/media/common/ir-keymaps.c	Wed Dec 20 10:07:33 2006 -0300
@@ -1704,3 +1704,88 @@ IR_KEYTAB_TYPE ir_codes_asus_pc39[IR_KEY
 };
 
 EXPORT_SYMBOL_GPL(ir_codes_asus_pc39);
+
+
+/* Encore ENLTV-FM  - black plastic, white front cover with white glowing buttons
+    Juan Pablo Sormani <sorman@xxxxxxxxx> */
+IR_KEYTAB_TYPE ir_codes_encore_enltv[IR_KEYTAB_SIZE] = {
+
+	/* Power button does nothing, neither in Windows app,
+	 although it sends data (used for BIOS wakeup?) */
+	[ 0x0d ] = KEY_MUTE,
+
+	[ 0x1e ] = KEY_TV,
+	[ 0x00 ] = KEY_VIDEO,
+	[ 0x01 ] = KEY_AUDIO,		/* music */
+	[ 0x02 ] = KEY_MHP,		/* picture */
+
+	[ 0x1f ] = KEY_1,
+	[ 0x03 ] = KEY_2,
+	[ 0x04 ] = KEY_3,
+	[ 0x05 ] = KEY_4,
+	[ 0x1c ] = KEY_5,
+	[ 0x06 ] = KEY_6,
+	[ 0x07 ] = KEY_7,
+	[ 0x08 ] = KEY_8,
+	[ 0x1d ] = KEY_9,
+	[ 0x0a ] = KEY_0,
+	
+	[ 0x09 ] = KEY_LIST,        /* -/-- */
+	[ 0x0b ] = KEY_LAST,        /* recall */
+
+	[ 0x14 ] = KEY_HOME,		/* win start menu */
+	[ 0x15 ] = KEY_EXIT,		/* exit */
+#if 0
+	[ 0x16 ] = KEY_CHANNELUP,	/* UP */
+	[ 0x12 ] = KEY_CHANNELDOWN,	/* DOWN */
+	[ 0x0c ] = KEY_VOLUMEUP,	/* RIGHT */
+	[ 0x17 ] = KEY_VOLUMEDOWN,	/* LEFT */
+#else
+	[ 0x16 ] = KEY_UP,
+	[ 0x12 ] = KEY_DOWN,
+	[ 0x0c ] = KEY_RIGHT,
+	[ 0x17 ] = KEY_LEFT,
+#endif
+
+	[ 0x18 ] = KEY_ENTER,		/* OK */
+
+	[ 0x0e ] = KEY_ESC,
+	[ 0x13 ] = KEY_D,		/* desktop */
+	[ 0x11 ] = KEY_TAB,
+	[ 0x19 ] = KEY_SWITCHVIDEOMODE,	/* switch */
+	
+	[ 0x1a ] = KEY_MENU,
+	[ 0x1b ] = KEY_ZOOM,		/* fullscreen */
+	[ 0x44 ] = KEY_TIME,		/* time shift */
+	[ 0x40 ] = KEY_MODE,		/* source */
+
+	[ 0x5a ] = KEY_RECORD,
+	[ 0x42 ] = KEY_PLAY,		/* play/pause */
+	[ 0x45 ] = KEY_STOP,
+	[ 0x43 ] = KEY_CAMERA,		/* camera icon */
+
+	[ 0x48 ] = KEY_REWIND,
+	[ 0x4a ] = KEY_FASTFORWARD,
+	[ 0x49 ] = KEY_PREVIOUS,
+	[ 0x4b ] = KEY_NEXT,
+
+	[ 0x4c ] = KEY_FAVORITES,	/* tv wall */
+	[ 0x4d ] = KEY_SOUND,		/* DVD sound */
+	[ 0x4e ] = KEY_LANGUAGE,	/* DVD lang */
+	[ 0x4f ] = KEY_TEXT,		/* DVD text */
+
+	[ 0x50 ] = KEY_SLEEP,		/* shutdown */
+	[ 0x51 ] = KEY_MODE,		/* stereo > main */
+	[ 0x52 ] = KEY_SELECT,		/* stereo > sap */
+	[ 0x53 ] = KEY_PROG1,		/* teletext */
+
+
+	[ 0x59 ] = KEY_RED,		/* AP1 */
+	[ 0x41 ] = KEY_GREEN,		/* AP2 */
+	[ 0x47 ] = KEY_YELLOW,		/* AP3 */
+	[ 0x57 ] = KEY_BLUE,		/* AP4 */
+
+
+};
+
+EXPORT_SYMBOL_GPL(ir_codes_encore_enltv);
diff -r d271c9d20d45 linux/drivers/media/video/saa7134/saa7134-cards.c
--- a/linux/drivers/media/video/saa7134/saa7134-cards.c	Thu Dec 21 17:07:08 2006 -0200
+++ b/linux/drivers/media/video/saa7134/saa7134-cards.c	Wed Dec 20 11:53:06 2006 -0300
@@ -3223,8 +3223,10 @@ struct saa7134_board saa7134_boards[] = 
 		}},
 	},
 	[SAA7134_BOARD_ENCORE_ENLTV] = {
-		/* Steven Walter <stevenrwalter@xxxxxxxxx> */
+	/* Steven Walter <stevenrwalter@xxxxxxxxx>
+	   Juan Pablo Sormani <sorman@xxxxxxxxx> */
 		.name           = "Encore ENLTV",
+		.audio_clock    = 0x00200000,
 		.tuner_type     = TUNER_TNF_5335MF,
 		.radio_type     = UNSET,
 		.tuner_addr	= ADDR_UNSET,
@@ -3232,13 +3234,71 @@ struct saa7134_board saa7134_boards[] = 
 		.inputs         = {{
 			.name = name_tv,
 			.vmux = 1,
-			.amux = LINE2,
-			.tv   = 1,
-		},{
-			.name = name_svideo,
-			.vmux = 6,
-			.amux = LINE1,
-		}},
+			.amux = 3,
+			.tv   = 1,
+		},{
+			.name = name_tv_mono,
+			.vmux = 7,
+			.amux = 4,
+			.tv   = 1,
+		},{
+			.name = name_comp1,
+			.vmux = 3,
+			.amux = 2,
+		},{
+			.name = name_svideo,
+			.vmux = 0,
+			.amux = 2,
+		}},
+		.radio = {
+			.name = name_radio,
+			.amux = LINE2,
+/*			.gpio = 0x00300001,*/
+			.gpio = 0x20000,
+
+		},
+		.mute = {
+			.name = name_mute,
+			.amux = 0,
+		},
+	},
+	[SAA7134_BOARD_ENCORE_ENLTV_FM] = {
+  /*	Juan Pablo Sormani <sorman@xxxxxxxxx> */
+		.name           = "Encore ENLTV-FM",
+		.audio_clock    = 0x00200000,
+		.tuner_type     = TUNER_PHILIPS_ATSC,
+		.radio_type     = UNSET,
+		.tuner_addr	= ADDR_UNSET,
+		.radio_addr	= ADDR_UNSET,
+		.inputs         = {{
+			.name = name_tv,
+			.vmux = 1,
+			.amux = 3,
+			.tv   = 1,
+		},{
+			.name = name_tv_mono,
+			.vmux = 7,
+			.amux = 4,
+			.tv   = 1,
+		},{
+			.name = name_comp1,
+			.vmux = 3,
+			.amux = 2,
+		},{
+			.name = name_svideo,
+			.vmux = 0,
+			.amux = 2,
+		}},
+		.radio = {
+			.name = name_radio,
+			.amux = LINE2,
+			.gpio = 0x20000,
+
+		},
+		.mute = {
+			.name = name_mute,
+			.amux = 0,
+		},
 	},
 };
 
@@ -3884,6 +3944,24 @@ struct pci_device_id saa7134_pci_tbl[] =
 		.subvendor    = PCI_VENDOR_ID_PHILIPS,
 		.subdevice    = 0x2342,
 		.driver_data  = SAA7134_BOARD_ENCORE_ENLTV,
+	},{
+		.vendor       = PCI_VENDOR_ID_PHILIPS,
+		.device       = PCI_DEVICE_ID_PHILIPS_SAA7130,
+		.subvendor    = 0x1131,
+		.subdevice    = 0x2341,
+		.driver_data  = SAA7134_BOARD_ENCORE_ENLTV,
+	},{
+		.vendor       = PCI_VENDOR_ID_PHILIPS,
+		.device       = PCI_DEVICE_ID_PHILIPS_SAA7130,
+		.subvendor    = 0x3016,
+		.subdevice    = 0x2344,
+		.driver_data  = SAA7134_BOARD_ENCORE_ENLTV,
+	},{
+		.vendor       = PCI_VENDOR_ID_PHILIPS,
+		.device       = PCI_DEVICE_ID_PHILIPS_SAA7130,
+		.subvendor    = 0x1131,
+		.subdevice    = 0x230f,
+		.driver_data  = SAA7134_BOARD_ENCORE_ENLTV_FM,
 	},{
 		/* --- boards without eeprom + subsystem ID --- */
 		.vendor       = PCI_VENDOR_ID_PHILIPS,
@@ -4030,6 +4108,8 @@ int saa7134_board_init1(struct saa7134_d
 	case SAA7134_BOARD_FLYDVBTDUO:
 	case SAA7134_BOARD_PROTEUS_2309:
 	case SAA7134_BOARD_AVERMEDIA_A16AR:
+	case SAA7134_BOARD_ENCORE_ENLTV:
+	case SAA7134_BOARD_ENCORE_ENLTV_FM:
 		dev->has_remote = SAA7134_REMOTE_GPIO;
 		break;
 	case SAA7134_BOARD_FLYDVBS_LR300:
diff -r d271c9d20d45 linux/drivers/media/video/saa7134/saa7134-input.c
--- a/linux/drivers/media/video/saa7134/saa7134-input.c	Thu Dec 21 17:07:08 2006 -0200
+++ b/linux/drivers/media/video/saa7134/saa7134-input.c	Wed Dec 20 11:16:19 2006 -0300
@@ -327,6 +327,13 @@ int saa7134_input_init1(struct saa7134_d
 		mask_keydown = 0x0040000;
 		rc5_gpio = 1;
 		break;
+	case SAA7134_BOARD_ENCORE_ENLTV:
+	case SAA7134_BOARD_ENCORE_ENLTV_FM:
+		ir_codes     = ir_codes_encore_enltv;
+		mask_keycode = 0x00007f;
+		mask_keyup   = 0x040000;
+		polling      = 50; // ms
+		break;
 	}
 	if (NULL == ir_codes) {
 		printk("%s: Oops: IR config error [card=%d]\n",
diff -r d271c9d20d45 linux/drivers/media/video/saa7134/saa7134.h
--- a/linux/drivers/media/video/saa7134/saa7134.h	Thu Dec 21 17:07:08 2006 -0200
+++ b/linux/drivers/media/video/saa7134/saa7134.h	Wed Dec 20 11:15:25 2006 -0300
@@ -242,6 +242,7 @@ struct saa7134_format {
 #define SAA7134_BOARD_HAUPPAUGE_HVR1110    104
 #define SAA7134_BOARD_CINERGY_HT_PCMCIA    105
 #define SAA7134_BOARD_ENCORE_ENLTV         106
+#define SAA7134_BOARD_ENCORE_ENLTV_FM      107
 
 #define SAA7134_MAXBOARDS 8
 #define SAA7134_INPUT_MAX 8
diff -r d271c9d20d45 linux/include/media/ir-common.h
--- a/linux/include/media/ir-common.h	Thu Dec 21 17:07:08 2006 -0200
+++ b/linux/include/media/ir-common.h	Fri Dec 22 12:25:53 2006 -0300
@@ -141,6 +141,7 @@ extern IR_KEYTAB_TYPE ir_codes_proteus_2
 extern IR_KEYTAB_TYPE ir_codes_proteus_2309[IR_KEYTAB_SIZE];
 extern IR_KEYTAB_TYPE ir_codes_budget_ci_old[IR_KEYTAB_SIZE];
 extern IR_KEYTAB_TYPE ir_codes_asus_pc39[IR_KEYTAB_SIZE];
+extern IR_KEYTAB_TYPE ir_codes_encore_enltv[IR_KEYTAB_SIZE];
 
 #endif
 

--
video4linux-list mailing list
Unsubscribe mailto:video4linux-list-request@xxxxxxxxxx?subject=unsubscribe
[https://www.redhat.com/mailman/listinfo/video4linux-list](https://www.redhat.com/mailman/listinfo/video4linux-list)

    * References:
          o [PATCH] Encore ENLTV-FM
                + From: sorman
          o Re: [PATCH] Encore ENLTV-FM
                + From: Mauro Carvalho Chehab
          o Re: [PATCH] Encore ENLTV-FM
                + From: sorman
          o Re: [PATCH] Encore ENLTV-FM
                + From: sorman

    * Prev by Date: Re: [PATCH] CX88 Chroma frequency fixes - Experimental
    * Next by Date: Re: New control identifiers
    * Previous by thread: Re: [PATCH] Encore ENLTV-FM
    * Next by thread: ATI TV Wonder Elite
    * Index(es):
          o Date
          o Thread

---

### Post by cpaulin on 2007-03-15
LOL I got the remote to work by modding the driver with the info I posted from the patch and recompiling the kernel but the video is now broken.  ARRRRGH

---

### Post by cpaulin on 2007-03-15
I just needed to set the tuner=69 in modprob. Now video and remote work all for $32 bucks and three weeks of recompiling the kernel. But the card is fully functional.

---

### Post by loganfre on 2007-11-26
where is the driver file that you edited? You will have to forgive me if this is obvious, I am VERY new to Ubuntu and Linux.

---

