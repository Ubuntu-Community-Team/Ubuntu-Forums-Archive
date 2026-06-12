---
title: "Hauppauge HVR-4000 and mythbuntu: firmware do not load, help"
date: 2009-04-26
forum: Multimedia Software
---

### Post by vinalopo on 2009-04-26
Hi! I am a new in using linux and in mythbuntu.
Have built a mythbox and I cant make my Hauppauage HVR-4000 works, have read any post on similar topic but I could not solve my issue.
Have followed linuxtv and eurocardsharing fora and it seems everything but driver loading ok

if I dmesg

I see

[INDENT][   20.854302] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[   20.854307] i2c-adapter i2c-0: firmware: requesting dvb-fe-cx24116.fw
[   20.926063] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[   22.144938] ppdev: user-space parallel port driver
[   25.668052] cx24116_cmd_execute() Firmware not responding
[   25.668055] cx24116_firmware_ondemand: Writing firmware to device failed
[   25.668065] cx24116_firmware_ondemand: Firmware upload failed
[   25.668066] cx24116_cmd_execute(): Unable initialise the firmware
[/INDENT]

how can I make the firware loading?

please help, thank u very much

---

### Post by pyroxer on 2009-04-27
same for me on 9.04 with Nova-HD-S2.  Can get logs later but similar to the above.

This was using firmware included in the ubuntu install.

---

### Post by viv2 on 2009-04-27
I am in the same boat. I had the card working with Kaffeine & Intrepid after a struggle (failed to get MythTV , Freevo, KDEplayer or any others to work), lost my screen so felt I had nothing to lose by going to Jaunty. Huh! Now the firmware does not load. I have tried blacklisting a couple of modules  -i2c and a duplicate mceusb2 and replacing a line as per below
--- v4l-dvb.orig/linux/drivers/media/dvb/frontends/cx24116.c    2009-03-01 16:09:08.000000000 +0100
+++ v4l-dvb/linux/drivers/media/dvb/frontends/cx24116.c    2009-04-26 09:52:02.000000000 +0200
@@ -492,7 +492,7 @@  static int cx24116_firmware_ondemand(str
         printk(KERN_INFO "%s: Waiting for firmware upload (%s)...\n",
             __func__, CX24116_DEFAULT_FIRMWARE);
         ret = request_firmware(&fw, CX24116_DEFAULT_FIRMWARE,
-            &state->i2c->dev);
+            state->i2c->dev.parent);
         printk(KERN_INFO "%s: Waiting for firmware upload(2)...\n",
             __func__);
         if (ret) {

Nothing working so far!

I am a linux newbie having been encouraged by my success with eeepc running easy peasy
 - the card works so-so under XP mythportal but I have found linux TV really a challenge. 
I may have overegged the drivers as I used the linuxtv-org HVR4000 wiki to pull down v4l-dvb.
My installed modules are

kernel/sound/i2c/snd-i2c.ko
kernel/sound/drivers/snd-dummy.ko
kernel/sound/drivers/snd-virmidi.ko
kernel/sound/drivers/snd-serial-u16550.ko
kernel/sound/drivers/snd-mtpav.ko
kernel/sound/drivers/snd-mts64.ko
kernel/sound/drivers/snd-portman2x4.ko
kernel/sound/drivers/opl3/snd-opl3-lib.ko
kernel/sound/drivers/opl3/snd-opl3-synth.ko
kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
kernel/sound/drivers/mpu401/snd-mpu401.ko
kernel/sound/drivers/vx/snd-vx-lib.ko
kernel/sound/drivers/pcsp/snd-pcsp.ko
kernel/sound/isa/sb/snd-sb-common.ko
kernel/sound/isa/sb/snd-sb16-dsp.ko
kernel/sound/pci/snd-ad1889.ko
kernel/sound/pci/snd-als300.ko
kernel/sound/pci/snd-als4000.ko
kernel/sound/pci/snd-atiixp.ko
kernel/sound/pci/snd-atiixp-modem.ko
kernel/sound/pci/snd-azt3328.ko
kernel/sound/pci/snd-bt87x.ko
kernel/sound/pci/snd-cmipci.ko
kernel/sound/pci/snd-cs4281.ko
kernel/sound/pci/snd-cs5530.ko
kernel/sound/pci/snd-ens1370.ko
kernel/sound/pci/snd-ens1371.ko
kernel/sound/pci/snd-es1938.ko
kernel/sound/pci/snd-es1968.ko
kernel/sound/pci/snd-fm801.ko
kernel/sound/pci/snd-intel8x0.ko
kernel/sound/pci/snd-intel8x0m.ko
kernel/sound/pci/snd-maestro3.ko
kernel/sound/pci/snd-rme32.ko
kernel/sound/pci/snd-rme96.ko
kernel/sound/pci/snd-sonicvibes.ko
kernel/sound/pci/snd-via82xx.ko
kernel/sound/pci/snd-via82xx-modem.ko
kernel/sound/pci/ac97/snd-ac97-codec.ko
kernel/sound/pci/ali5451/snd-ali5451.ko
kernel/sound/pci/au88x0/snd-au8810.ko
kernel/sound/pci/au88x0/snd-au8820.ko
kernel/sound/pci/au88x0/snd-au8830.ko
kernel/sound/pci/aw2/snd-aw2.ko
kernel/sound/pci/ca0106/snd-ca0106.ko
kernel/sound/pci/cs46xx/snd-cs46xx.ko
kernel/sound/pci/echoaudio/snd-darla20.ko
kernel/sound/pci/echoaudio/snd-gina20.ko
kernel/sound/pci/echoaudio/snd-layla20.ko
kernel/sound/pci/echoaudio/snd-darla24.ko
kernel/sound/pci/echoaudio/snd-gina24.ko
kernel/sound/pci/echoaudio/snd-layla24.ko
kernel/sound/pci/echoaudio/snd-mona.ko
kernel/sound/pci/echoaudio/snd-mia.ko
kernel/sound/pci/echoaudio/snd-echo3g.ko
kernel/sound/pci/echoaudio/snd-indigo.ko
kernel/sound/pci/echoaudio/snd-indigoio.ko
kernel/sound/pci/echoaudio/snd-indigodj.ko
kernel/sound/pci/emu10k1/snd-emu10k1.ko
kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
kernel/sound/pci/emu10k1/snd-emu10k1x.ko
kernel/sound/pci/hda/snd-hda-intel.ko
kernel/sound/pci/ice1712/snd-ice1712.ko
kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
kernel/sound/pci/ice1712/snd-ice1724.ko
kernel/sound/pci/korg1212/snd-korg1212.ko
kernel/sound/pci/mixart/snd-mixart.ko
kernel/sound/pci/nm256/snd-nm256.ko
kernel/sound/pci/oxygen/snd-oxygen-lib.ko
kernel/sound/pci/oxygen/snd-hifier.ko
kernel/sound/pci/oxygen/snd-oxygen.ko
kernel/sound/pci/oxygen/snd-virtuoso.ko
kernel/sound/pci/pcxhr/snd-pcxhr.ko
kernel/sound/pci/riptide/snd-riptide.ko
kernel/sound/pci/rme9652/snd-rme9652.ko
kernel/sound/pci/rme9652/snd-hdsp.ko
kernel/sound/pci/rme9652/snd-hdspm.ko
kernel/sound/pci/trident/snd-trident.ko
kernel/sound/pci/ymfpci/snd-ymfpci.ko
kernel/sound/pci/vx222/snd-vx222.ko
kernel/sound/synth/snd-util-mem.ko
kernel/sound/synth/emux/snd-emux-synth.ko
kernel/sound/usb/snd-usb-audio.ko
kernel/sound/usb/snd-usb-lib.ko
kernel/sound/usb/usx2y/snd-usb-usx2y.ko
kernel/sound/usb/usx2y/snd-usb-us122l.ko
kernel/sound/usb/caiaq/snd-usb-caiaq.ko
kernel/sound/pcmcia/vx/snd-vxpocket.ko
kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
kernel/sound/soc/snd-soc-core.ko
kernel/sound/soc/codecs/snd-soc-ad73311.ko
kernel/sound/soc/codecs/snd-soc-ak4535.ko
kernel/sound/soc/codecs/snd-soc-cs4270.ko
kernel/sound/soc/codecs/snd-soc-ssm2602.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
kernel/sound/soc/codecs/snd-soc-uda1380.ko
kernel/sound/soc/codecs/snd-soc-wm8510.ko
kernel/sound/soc/codecs/snd-soc-wm8580.ko
kernel/sound/soc/codecs/snd-soc-wm8731.ko
kernel/sound/soc/codecs/snd-soc-wm8750.ko
kernel/sound/soc/codecs/snd-soc-wm8753.ko
kernel/sound/soc/codecs/snd-soc-wm8900.ko
kernel/sound/soc/codecs/snd-soc-wm8903.ko
kernel/sound/soc/codecs/snd-soc-wm8971.ko
kernel/sound/soc/codecs/snd-soc-wm8990.ko
kernel/sound/ac97_bus.ko
kernel/ubuntu/drbd/drbd.ko
kernel/ubuntu/iscsitarget/iscsi_trgt.ko
kernel/ubuntu/squashfs/squashfs.ko
kernel/ubuntu/aufs/aufs.ko
kernel/ubuntu/et131x/et131x.ko
kernel/ubuntu/dm-raid4-5/dm-raid4-5.ko
kernel/ubuntu/dm-raid4-5/dm-mem-cache.ko
kernel/ubuntu/dm-raid4-5/dm-region_hash.ko
kernel/ubuntu/dm-raid4-5/dm-message.ko
kernel/ubuntu/dm-loop/dm-loop.ko
kernel/ubuntu/ndiswrapper/ndiswrapper.ko
kernel/ubuntu/compcache/compcache.ko
kernel/ubuntu/compcache/tlsf.ko
kernel/ubuntu/heci/heci.ko
kernel/ubuntu/qc-usb/quickcam.ko
kernel/ubuntu/unionfs/unionfs.ko
kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko
kernel/ubuntu/lirc/lirc_atiusb/lirc_atiusb.ko
kernel/ubuntu/lirc/lirc_bt829/lirc_bt829.ko
kernel/ubuntu/lirc/lirc_cmdir/lirc_cmdir.ko
kernel/ubuntu/lirc/lirc_cmdir/commandir.ko
kernel/ubuntu/lirc/lirc_i2c/lirc_i2c.ko
kernel/ubuntu/lirc/lirc_igorplugusb/lirc_igorplugusb.ko
kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko
kernel/ubuntu/lirc/lirc_it87/lirc_it87.ko
kernel/ubuntu/lirc/lirc_mceusb/lirc_mceusb.ko
kernel/ubuntu/lirc/lirc_mceusb2/lirc_mceusb2.ko
kernel/ubuntu/lirc/lirc_pvr150/lirc_pvr150.ko
kernel/ubuntu/lirc/lirc_sasem/lirc_sasem.ko
kernel/ubuntu/lirc/lirc_serial/lirc_serial.ko
kernel/ubuntu/lirc/lirc_serial_igor/lirc_serial_igor.ko
kernel/ubuntu/lirc/lirc_sir/lirc_sir.ko
kernel/ubuntu/lirc/lirc_streamzap/lirc_streamzap.ko
kernel/ubuntu/lirc/lirc_ttusbir/lirc_ttusbir.ko
kernel/ubuntu/lirc/lirc_gpio/lirc_gpio.ko
kernel/ubuntu/misc/appleir.ko
kernel/ubuntu/misc/dm-bbr.ko
kernel/ubuntu/misc/lmpcm_usb.ko
kernel/ubuntu/misc/tp_smapi.ko
kernel/ubuntu/misc/thinkpad_ec.ko
kernel/ubuntu/misc/fsam7400.ko
kernel/ubuntu/misc/media/ov511/ov511_decomp.ko
kernel/ubuntu/misc/media/ov511/ov518_decomp.ko
kernel/ubuntu/misc/wireless/acx/acx.ko
kernel/ubuntu/misc/wireless/p80211/p80211.ko
kernel/ubuntu/rfkill/av5100.ko
kernel/ubuntu/rfkill/pbe5.ko
kernel/arch/x86/oprofile/oprofile.ko
kernel/net/core/pktgen.ko
kernel/net/llc/llc2.ko
kernel/net/802/p8023.ko
kernel/net/802/stp.ko
kernel/net/802/garp.ko
kernel/net/sched/act_police.ko
kernel/net/sched/act_gact.ko
kernel/net/sched/act_mirred.ko
kernel/net/sched/act_ipt.ko
kernel/net/sched/act_nat.ko
kernel/net/sched/act_pedit.ko
kernel/net/sched/act_simple.ko
kernel/net/sched/act_skbedit.ko
kernel/net/sched/sch_cbq.ko
kernel/net/sched/sch_htb.ko
kernel/net/sched/sch_hfsc.ko
kernel/net/sched/sch_red.ko
kernel/net/sched/sch_gred.ko
kernel/net/sched/sch_ingress.ko
kernel/net/sched/sch_dsmark.ko
kernel/net/sched/sch_sfq.ko
kernel/net/sched/sch_tbf.ko
kernel/net/sched/sch_teql.ko
kernel/net/sched/sch_prio.ko
kernel/net/sched/sch_multiq.ko
kernel/net/sched/sch_atm.ko
kernel/net/sched/sch_netem.ko
kernel/net/sched/cls_u32.ko
kernel/net/sched/cls_route.ko
kernel/net/sched/cls_fw.ko
kernel/net/sched/cls_rsvp.ko
kernel/net/sched/cls_tcindex.ko
kernel/net/sched/cls_rsvp6.ko
kernel/net/sched/cls_basic.ko
kernel/net/sched/em_cmp.ko
kernel/net/sched/em_nbyte.ko
kernel/net/sched/em_u32.ko
kernel/net/sched/em_meta.ko
kernel/net/sched/em_text.ko
kernel/net/netfilter/nfnetlink.ko
kernel/net/netfilter/nfnetlink_queue.ko
kernel/net/netfilter/nfnetlink_log.ko
kernel/net/netfilter/nf_conntrack.ko
kernel/net/netfilter/nf_conntrack_proto_gre.ko
kernel/net/netfilter/nf_conntrack_proto_sctp.ko
kernel/net/netfilter/nf_conntrack_proto_udplite.ko
kernel/net/netfilter/nf_conntrack_netlink.ko
kernel/net/netfilter/nf_conntrack_amanda.ko
kernel/net/netfilter/nf_conntrack_ftp.ko
kernel/net/netfilter/nf_conntrack_h323.ko
kernel/net/netfilter/nf_conntrack_irc.ko
kernel/net/netfilter/nf_conntrack_netbios_ns.ko
kernel/net/netfilter/nf_conntrack_pptp.ko
kernel/net/netfilter/nf_conntrack_sip.ko
kernel/net/netfilter/nf_conntrack_tftp.ko
kernel/net/netfilter/nf_tproxy_core.ko
kernel/net/netfilter/x_tables.ko
kernel/net/netfilter/xt_tcpudp.ko
kernel/net/netfilter/xt_CLASSIFY.ko
kernel/net/netfilter/xt_CONNMARK.ko
kernel/net/netfilter/xt_CONNSECMARK.ko
kernel/net/netfilter/xt_DSCP.ko
kernel/net/netfilter/xt_MARK.ko
kernel/net/netfilter/xt_NFLOG.ko
kernel/net/netfilter/xt_NFQUEUE.ko
kernel/net/netfilter/xt_NOTRACK.ko
kernel/net/netfilter/xt_RATEEST.ko
kernel/net/netfilter/xt_SECMARK.ko
kernel/net/netfilter/xt_TPROXY.ko
kernel/net/netfilter/xt_TCPMSS.ko
kernel/net/netfilter/xt_TRACE.ko
kernel/net/netfilter/xt_comment.ko
kernel/net/netfilter/xt_connbytes.ko
kernel/net/netfilter/xt_connlimit.ko
kernel/net/netfilter/xt_connmark.ko
kernel/net/netfilter/xt_conntrack.ko
kernel/net/netfilter/xt_dccp.ko
kernel/net/netfilter/xt_dscp.ko
kernel/net/netfilter/xt_esp.ko
kernel/net/netfilter/xt_hashlimit.ko
kernel/net/netfilter/xt_helper.ko
kernel/net/netfilter/xt_iprange.ko
kernel/net/netfilter/xt_length.ko
kernel/net/netfilter/xt_limit.ko
kernel/net/netfilter/xt_mac.ko
kernel/net/netfilter/xt_mark.ko
kernel/net/netfilter/xt_multiport.ko
kernel/net/netfilter/xt_owner.ko
kernel/net/netfilter/xt_physdev.ko
kernel/net/netfilter/xt_pkttype.ko
kernel/net/netfilter/xt_policy.ko
kernel/net/netfilter/xt_quota.ko
kernel/net/netfilter/xt_rateest.ko
kernel/net/netfilter/xt_realm.ko
kernel/net/netfilter/xt_recent.ko
kernel/net/netfilter/xt_sctp.ko
kernel/net/netfilter/xt_socket.ko
kernel/net/netfilter/xt_state.ko
kernel/net/netfilter/xt_statistic.ko
kernel/net/netfilter/xt_string.ko
kernel/net/netfilter/xt_tcpmss.ko
kernel/net/netfilter/xt_time.ko
kernel/net/netfilter/xt_u32.ko
kernel/net/netfilter/ipvs/ip_vs.ko
kernel/net/netfilter/ipvs/ip_vs_rr.ko
kernel/net/netfilter/ipvs/ip_vs_wrr.ko
kernel/net/netfilter/ipvs/ip_vs_lc.ko
kernel/net/netfilter/ipvs/ip_vs_wlc.ko
kernel/net/netfilter/ipvs/ip_vs_lblc.ko
kernel/net/netfilter/ipvs/ip_vs_lblcr.ko
kernel/net/netfilter/ipvs/ip_vs_dh.ko
kernel/net/netfilter/ipvs/ip_vs_sh.ko
kernel/net/netfilter/ipvs/ip_vs_sed.ko
kernel/net/netfilter/ipvs/ip_vs_nq.ko
kernel/net/netfilter/ipvs/ip_vs_ftp.ko
kernel/net/ipv4/netfilter/nf_conntrack_ipv4.ko
kernel/net/ipv4/netfilter/nf_nat.ko
kernel/net/ipv4/netfilter/nf_defrag_ipv4.ko
kernel/net/ipv4/netfilter/nf_nat_amanda.ko
kernel/net/ipv4/netfilter/nf_nat_ftp.ko
kernel/net/ipv4/netfilter/nf_nat_h323.ko
kernel/net/ipv4/netfilter/nf_nat_irc.ko
kernel/net/ipv4/netfilter/nf_nat_pptp.ko
kernel/net/ipv4/netfilter/nf_nat_sip.ko
kernel/net/ipv4/netfilter/nf_nat_snmp_basic.ko
kernel/net/ipv4/netfilter/nf_nat_tftp.ko
kernel/net/ipv4/netfilter/nf_nat_proto_gre.ko
kernel/net/ipv4/netfilter/nf_nat_proto_udplite.ko
kernel/net/ipv4/netfilter/nf_nat_proto_sctp.ko
kernel/net/ipv4/netfilter/ip_tables.ko
kernel/net/ipv4/netfilter/iptable_filter.ko
kernel/net/ipv4/netfilter/iptable_mangle.ko
kernel/net/ipv4/netfilter/iptable_nat.ko
kernel/net/ipv4/netfilter/iptable_raw.ko
kernel/net/ipv4/netfilter/iptable_security.ko
kernel/net/ipv4/netfilter/ipt_addrtype.ko
kernel/net/ipv4/netfilter/ipt_ah.ko
kernel/net/ipv4/netfilter/ipt_ecn.ko
kernel/net/ipv4/netfilter/ipt_ttl.ko
kernel/net/ipv4/netfilter/ipt_CLUSTERIP.ko
kernel/net/ipv4/netfilter/ipt_ECN.ko
kernel/net/ipv4/netfilter/ipt_LOG.ko
kernel/net/ipv4/netfilter/ipt_MASQUERADE.ko
kernel/net/ipv4/netfilter/ipt_NETMAP.ko
kernel/net/ipv4/netfilter/ipt_REDIRECT.ko
kernel/net/ipv4/netfilter/ipt_REJECT.ko
kernel/net/ipv4/netfilter/ipt_TTL.ko
kernel/net/ipv4/netfilter/ipt_ULOG.ko
kernel/net/ipv4/netfilter/arp_tables.ko
kernel/net/ipv4/netfilter/arpt_mangle.ko
kernel/net/ipv4/netfilter/arptable_filter.ko
kernel/net/ipv4/netfilter/ip_queue.ko
kernel/net/ipv4/ipip.ko
kernel/net/ipv4/ip_gre.ko
kernel/net/ipv4/ah4.ko
kernel/net/ipv4/esp4.ko
kernel/net/ipv4/ipcomp.ko
kernel/net/ipv4/xfrm4_tunnel.ko
kernel/net/ipv4/xfrm4_mode_beet.ko
kernel/net/ipv4/inet_lro.ko
kernel/net/ipv4/tunnel4.ko
kernel/net/ipv4/xfrm4_mode_transport.ko
kernel/net/ipv4/xfrm4_mode_tunnel.ko
kernel/net/ipv4/tcp_probe.ko
kernel/net/ipv4/tcp_bic.ko
kernel/net/ipv4/tcp_westwood.ko
kernel/net/ipv4/tcp_highspeed.ko
kernel/net/ipv4/tcp_hybla.ko
kernel/net/ipv4/tcp_htcp.ko
kernel/net/ipv4/tcp_vegas.ko
kernel/net/ipv4/tcp_veno.ko
kernel/net/ipv4/tcp_scalable.ko
kernel/net/ipv4/tcp_lp.ko
kernel/net/ipv4/tcp_yeah.ko
kernel/net/ipv4/tcp_illinois.ko
kernel/net/xfrm/xfrm_user.ko
kernel/net/xfrm/xfrm_ipcomp.ko
kernel/net/ipv6/netfilter/ip6_tables.ko
kernel/net/ipv6/netfilter/ip6table_filter.ko
kernel/net/ipv6/netfilter/ip6table_mangle.ko
kernel/net/ipv6/netfilter/ip6_queue.ko
kernel/net/ipv6/netfilter/ip6table_raw.ko
kernel/net/ipv6/netfilter/ip6table_security.ko
kernel/net/ipv6/netfilter/nf_conntrack_ipv6.ko
kernel/net/ipv6/netfilter/ip6t_ah.ko
kernel/net/ipv6/netfilter/ip6t_eui64.ko
kernel/net/ipv6/netfilter/ip6t_frag.ko
kernel/net/ipv6/netfilter/ip6t_hl.ko
kernel/net/ipv6/netfilter/ip6t_ipv6header.ko
kernel/net/ipv6/netfilter/ip6t_mh.ko
kernel/net/ipv6/netfilter/ip6t_hbh.ko
kernel/net/ipv6/netfilter/ip6t_rt.ko
kernel/net/ipv6/netfilter/ip6t_HL.ko
kernel/net/ipv6/netfilter/ip6t_LOG.ko
kernel/net/ipv6/netfilter/ip6t_REJECT.ko
kernel/net/ipv6/ah6.ko
kernel/net/ipv6/esp6.ko
kernel/net/ipv6/ipcomp6.ko
kernel/net/ipv6/xfrm6_tunnel.ko
kernel/net/ipv6/tunnel6.ko
kernel/net/ipv6/xfrm6_mode_transport.ko
kernel/net/ipv6/xfrm6_mode_tunnel.ko
kernel/net/ipv6/xfrm6_mode_ro.ko
kernel/net/ipv6/xfrm6_mode_beet.ko
kernel/net/ipv6/sit.ko
kernel/net/ipv6/ip6_tunnel.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/net/bluetooth/hidp/hidp.ko
kernel/net/atm/br2684.ko
kernel/net/atm/lec.ko
kernel/net/atm/mpoa.ko
kernel/net/atm/pppoatm.ko
kernel/net/8021q/8021q.ko
kernel/net/wireless/cfg80211.ko
kernel/net/rfkill/rfkill-input.ko
kernel/net/key/af_key.ko
kernel/net/bridge/bridge.ko
kernel/net/bridge/netfilter/ebtables.ko
kernel/net/bridge/netfilter/ebtable_broute.ko
kernel/net/bridge/netfilter/ebtable_filter.ko
kernel/net/bridge/netfilter/ebtable_nat.ko
kernel/net/bridge/netfilter/ebt_802_3.ko
kernel/net/bridge/netfilter/ebt_among.ko
kernel/net/bridge/netfilter/ebt_arp.ko
kernel/net/bridge/netfilter/ebt_ip.ko
kernel/net/bridge/netfilter/ebt_ip6.ko
kernel/net/bridge/netfilter/ebt_limit.ko
kernel/net/bridge/netfilter/ebt_mark_m.ko
kernel/net/bridge/netfilter/ebt_pkttype.ko
kernel/net/bridge/netfilter/ebt_stp.ko
kernel/net/bridge/netfilter/ebt_vlan.ko
kernel/net/bridge/netfilter/ebt_arpreply.ko
kernel/net/bridge/netfilter/ebt_mark.ko
kernel/net/bridge/netfilter/ebt_dnat.ko
kernel/net/bridge/netfilter/ebt_redirect.ko
kernel/net/bridge/netfilter/ebt_snat.ko
kernel/net/bridge/netfilter/ebt_log.ko
kernel/net/bridge/netfilter/ebt_ulog.ko
kernel/net/bridge/netfilter/ebt_nflog.ko
kernel/net/ipx/ipx.ko
kernel/net/appletalk/appletalk.ko
kernel/net/wanrouter/wanrouter.ko
kernel/net/x25/x25.ko
kernel/net/lapb/lapb.ko
kernel/net/netrom/netrom.ko
kernel/net/rose/rose.ko
kernel/net/ax25/ax25.ko
kernel/net/irda/irda.ko
kernel/net/irda/irlan/irlan.ko
kernel/net/irda/irnet/irnet.ko
kernel/net/irda/ircomm/ircomm.ko
kernel/net/irda/ircomm/ircomm-tty.ko
kernel/net/sunrpc/sunrpc.ko
kernel/net/sunrpc/auth_gss/auth_rpcgss.ko
kernel/net/sunrpc/auth_gss/rpcsec_gss_krb5.ko
kernel/net/sunrpc/auth_gss/rpcsec_gss_spkm3.ko
kernel/net/sunrpc/xprtrdma/xprtrdma.ko
kernel/net/sunrpc/xprtrdma/svcrdma.ko
kernel/net/rxrpc/af-rxrpc.ko
kernel/net/rxrpc/rxkad.ko
kernel/net/decnet/netfilter/dn_rtmsg.ko
kernel/net/decnet/decnet.ko
kernel/net/econet/econet.ko
kernel/net/phonet/phonet.ko
kernel/net/phonet/pn_pep.ko
kernel/net/dccp/ccids/lib/dccp_tfrc_lib.ko
kernel/net/dccp/ccids/dccp_ccid3.ko
kernel/net/dccp/ccids/dccp_ccid2.ko
kernel/net/dccp/dccp.ko
kernel/net/dccp/dccp_ipv4.ko
kernel/net/dccp/dccp_ipv6.ko
kernel/net/dccp/dccp_diag.ko
kernel/net/dccp/dccp_probe.ko
kernel/net/sctp/sctp.ko
kernel/net/mac80211/mac80211.ko
kernel/net/ieee80211/ieee80211.ko
kernel/net/ieee80211/ieee80211_crypt.ko
kernel/net/ieee80211/ieee80211_crypt_wep.ko
kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
kernel/net/ieee80211/ieee80211_crypt_tkip.ko
kernel/net/tipc/tipc.ko
kernel/net/9p/9pnet.ko
kernel/net/9p/9pnet_virtio.ko
kernel/net/9p/9pnet_rdma.ko
kernel/lib/crc-ccitt.ko
kernel/lib/crc-itu-t.ko
kernel/lib/crc7.ko
kernel/lib/libcrc32c.ko
kernel/lib/zlib_deflate/zlib_deflate.ko
kernel/lib/reed_solomon/reed_solomon.ko
kernel/lib/lzo/lzo_compress.ko
kernel/lib/lzo/lzo_decompress.ko
kernel/lib/ts_kmp.ko
kernel/lib/ts_bm.ko
kernel/lib/ts_fsm.ko
volatile/ath_hal.ko
volatile/ath_pci.ko
volatile/ath_rate_amrr.ko
volatile/ath_rate_minstrel.ko
volatile/ath_rate_onoe.ko
volatile/ath_rate_sample.ko
volatile/wl.ko
volatile/wlan.ko
volatile/wlan_acl.ko
volatile/wlan_ccmp.ko
volatile/wlan_scan_ap.ko
volatile/wlan_scan_sta.ko
volatile/wlan_tkip.ko
volatile/wlan_wep.ko
volatile/wlan_xauth.ko
kernel/drivers/media/radio/radio-tea5764.ko
kernel/drivers/media/common/tuners/mc44s803.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-ce6230.ko
kernel/drivers/media/dvb/frontends/stv6110.ko
kernel/drivers/media/dvb/frontends/stv0900.ko
kernel/drivers/media/dvb/frontends/stv6110x.ko
kernel/drivers/media/dvb/frontends/dvb_dummy_fe.ko
kernel/drivers/media/dvb/frontends/lgdt3305.ko
kernel/drivers/media/dvb/frontends/lgs8gxx.ko
kernel/drivers/media/dvb/frontends/lgdt3304.ko
kernel/drivers/media/dvb/frontends/s921.ko
kernel/drivers/media/dvb/frontends/cx24113.ko
kernel/drivers/media/dvb/frontends/stv090x.ko
kernel/drivers/media/dvb/frontends/zl10036.ko
kernel/drivers/media/dvb/frontends/stb6100.ko
kernel/drivers/media/dvb/frontends/isl6423.ko
kernel/drivers/media/dvb/frontends/tda8261.ko
kernel/drivers/media/dvb/frontends/stb0899.ko
kernel/drivers/media/dvb/siano/smsusb.ko
kernel/drivers/media/dvb/siano/smsdvb.ko
kernel/drivers/media/dvb/firewire/firedtv.ko
kernel/drivers/media/video/gspca/gspca_sq905.ko
kernel/drivers/media/video/gspca/gspca_sq905c.ko
kernel/drivers/media/video/gspca/gspca_ov534.ko
kernel/drivers/media/video/gspca/stv06xx/gspca_stv06xx.ko
kernel/drivers/media/video/gspca/gspca_mr97310a.ko
kernel/drivers/media/video/mt9t031.ko
kernel/drivers/media/video/dabusb.ko
kernel/drivers/media/video/cx231xx/cx231xx-dvb.ko
kernel/drivers/media/video/cx231xx/cx231xx-alsa.ko
kernel/drivers/media/video/cx231xx/cx231xx.ko
kernel/drivers/media/video/v4l2-compat-ioctl32.ko
kernel/drivers/media/video/ov772x.ko
kernel/drivers/media/video/tw9910.ko
kernel/drivers/media/video/tcm825x.ko
kernel/drivers/media/video/bt866.ko
kernel/drivers/media/video/ov511.ko
kernel/drivers/media/video/tvp514x.ko
kernel/drivers/media/video/hdpvr/hdpvr.ko
kernel/drivers/media/video/saa7191.ko
kernel/drivers/media/video/tlv320aic23b.ko
initrd/vesafb.ko
updates/dkms/nvidia.ko

and my dmesg

[    0.466631] ACPI: Interpreter enabled
[    0.466633] ACPI: (supports S0 S1 S3 S4 S5)
[    0.466648] ACPI: Using IOAPIC for interrupt routing
[    0.466696] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.524886] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.532597] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.591349] ACPI: No dock devices found.
[    0.591406] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.592316] pci 0000:00:03.0: reg 10 io port: [0x4f00-0x4fff]
[    0.592361] pci 0000:00:03.1: reg 10 io port: [0x4900-0x493f]
[    0.592373] pci 0000:00:03.1: reg 20 io port: [0x4d00-0x4d3f]
[    0.592378] pci 0000:00:03.1: reg 24 io port: [0x4e00-0x4e3f]
[    0.592389] pci 0000:00:03.1: PME# supported from D3hot D3cold
[    0.592394] pci 0000:00:03.1: PME# disabled
[    0.592455] pci 0000:00:03.3: reg 10 32bit mmio: [0xf9f80000-0xf9ffffff]
[    0.592627] pci 0000:00:04.0: reg 10 32bit mmio: [0xf9f7f000-0xf9f7ffff]
[    0.592650] pci 0000:00:04.0: supports D1 D2
[    0.592651] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.592654] pci 0000:00:04.0: PME# disabled
[    0.592680] pci 0000:00:04.1: reg 10 32bit mmio: [0xf9f7ec00-0xf9f7ecff]
[    0.592705] pci 0000:00:04.1: supports D1 D2
[    0.592706] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.592709] pci 0000:00:04.1: PME# disabled
[    0.592751] pci 0000:00:08.0: reg 20 io port: [0xffa0-0xffaf]
[    0.592787] pci 0000:00:09.0: reg 10 32bit mmio: [0xf9f78000-0xf9f7bfff]
[    0.592810] pci 0000:00:09.0: PME# supported from D3hot D3cold
[    0.592813] pci 0000:00:09.0: PME# disabled
[    0.592866] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.592868] pci 0000:00:0b.0: PME# disabled
[    0.592897] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.592900] pci 0000:00:0c.0: PME# disabled
[    0.592929] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.592931] pci 0000:00:0d.0: PME# disabled
[    0.592957] pci 0000:00:0e.0: reg 10 io port: [0xe480-0xe487]
[    0.592960] pci 0000:00:0e.0: reg 14 io port: [0xe400-0xe403]
[    0.592964] pci 0000:00:0e.0: reg 18 io port: [0xe080-0xe087]
[    0.592967] pci 0000:00:0e.0: reg 1c io port: [0xe000-0xe003]
[    0.592971] pci 0000:00:0e.0: reg 20 io port: [0xdc00-0xdc0f]
[    0.592975] pci 0000:00:0e.0: reg 24 32bit mmio: [0xf9f7c000-0xf9f7dfff]
[    0.593009] pci 0000:00:0f.0: reg 10 32bit mmio: [0xf9f77000-0xf9f77fff]
[    0.593013] pci 0000:00:0f.0: reg 14 io port: [0xd880-0xd887]
[    0.593016] pci 0000:00:0f.0: reg 18 32bit mmio: [0xf9f7e800-0xf9f7e8ff]
[    0.593020] pci 0000:00:0f.0: reg 1c 32bit mmio: [0xf9f7e400-0xf9f7e40f]
[    0.593034] pci 0000:00:0f.0: supports D1 D2
[    0.593035] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.593039] pci 0000:00:0f.0: PME# disabled
[    0.593061] pci 0000:00:10.0: reg 10 32bit mmio: [0xf8000000-0xf8ffffff]
[    0.593067] pci 0000:00:10.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.593072] pci 0000:00:10.0: reg 1c 64bit mmio: [0xf7000000-0xf7ffffff]
[    0.593078] pci 0000:00:10.0: reg 30 32bit mmio: [0xf9f40000-0xf9f5ffff]
[    0.593139] pci 0000:01:06.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.593195] pci 0000:01:06.1: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.593250] pci 0000:01:06.2: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.593307] pci 0000:01:06.4: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.593371] pci 0000:00:0a.0: transparent bridge
[    0.593375] pci 0000:00:0a.0: bridge 32bit mmio: [0xfa000000-0xfdffffff]
[    0.593516] bus 00 -> node 0
[    0.593522] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.593760] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.593933] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.594032] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.594129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    1.944486] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    1.944702] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    1.944920] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *10
[    1.945133] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    1.945345] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    1.945557] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    1.945768] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    1.945981] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    1.946196] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    1.946412] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    1.946631] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *7
[    1.946846] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *7
[    1.947061] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    1.947282] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    1.947501] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *7
[    1.947719] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    1.947970] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    1.948101] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 88, should be 85 [20080926]
[    1.948222] ACPI: WMI: Mapper loaded
[    1.948265] SCSI subsystem initialized
[    1.948265] libata version 3.00 loaded.
[    1.948265] usbcore: registered new interface driver usbfs
[    1.948265] usbcore: registered new interface driver hub
[    1.948265] usbcore: registered new device driver usb
[    1.948265] PCI: Using ACPI for IRQ routing
[    1.960016] Bluetooth: Core ver 2.13
[    1.960035] NET: Registered protocol family 31
[    1.960035] Bluetooth: HCI device and connection manager initialized
[    1.960035] Bluetooth: HCI socket layer initialized
[    1.960035] NET: Registered protocol family 8
[    1.960035] NET: Registered protocol family 20
[    1.960052] NetLabel: Initializing
[    1.960054] NetLabel:  domain hash size = 128
[    1.960056] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.960075] NetLabel:  unlabeled traffic allowed by default
[    1.960130] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    1.960133] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    1.964095] AppArmor: AppArmor Filesystem Enabled
[    1.968013] Switched to high resolution mode on CPU 0
[    1.968411] Switched to high resolution mode on CPU 1
[    1.976035] pnp: PnP ACPI init
[    1.976047] ACPI: bus type pnp registered
[    2.033340] pnp: PnP ACPI: found 15 devices
[    2.033341] ACPI: ACPI bus type pnp unregistered
[    2.033349] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    2.033351] system 00:06: ioport range 0x800-0x80f has been reserved
[    2.033353] system 00:06: ioport range 0x4000-0x407f has been reserved
[    2.033355] system 00:06: ioport range 0x4080-0x40ff has been reserved
[    2.033356] system 00:06: ioport range 0x4400-0x447f has been reserved
[    2.033358] system 00:06: ioport range 0x4480-0x44ff has been reserved
[    2.033359] system 00:06: ioport range 0x4800-0x487f has been reserved
[    2.033361] system 00:06: ioport range 0x4880-0x48ff has been reserved
[    2.033363] system 00:06: ioport range 0x4900-0x493f has been reserved
[    2.033364] system 00:06: ioport range 0x4c00-0x4c7f has been reserved
[    2.033366] system 00:06: ioport range 0x4c80-0x4cff has been reserved
[    2.033368] system 00:06: iomem range 0xfec80000-0xfed3ffff has been reserved
[    2.033370] system 00:06: iomem range 0xfed45000-0x1fd93ffff could not be reserved
[    2.033372] system 00:06: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    2.033373] system 00:06: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    2.033375] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[    2.033379] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    2.033381] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    2.033385] system 00:0c: ioport range 0xa00-0xa0f has been reserved
[    2.033394] system 00:0c: ioport range 0xa10-0xa1f has been reserved
[    2.033395] system 00:0c: ioport range 0xa20-0xa2f has been reserved
[    2.033397] system 00:0c: ioport range 0xa30-0xa3f has been reserved
[    2.033400] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    2.033404] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    2.033406] system 00:0e: iomem range 0xc0000-0xcffff has been reserved
[    2.033408] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    2.033409] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[    2.033411] system 00:0e: iomem range 0xfed45000-0xffffffff could not be reserved
[    2.038052] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
[    2.038053] pci 0000:00:0a.0:   IO window: disabled
[    2.038057] pci 0000:00:0a.0:   MEM window: 0xfa000000-0xfdffffff
[    2.038059] pci 0000:00:0a.0:   PREFETCH window: disabled
[    2.038063] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    2.038064] pci 0000:00:0b.0:   IO window: disabled
[    2.038067] pci 0000:00:0b.0:   MEM window: disabled
[    2.038069] pci 0000:00:0b.0:   PREFETCH window: disabled
[    2.038072] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    2.038073] pci 0000:00:0c.0:   IO window: disabled
[    2.038075] pci 0000:00:0c.0:   MEM window: disabled
[    2.038077] pci 0000:00:0c.0:   PREFETCH window: disabled
[    2.038081] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    2.038082] pci 0000:00:0d.0:   IO window: disabled
[    2.038084] pci 0000:00:0d.0:   MEM window: disabled
[    2.038086] pci 0000:00:0d.0:   PREFETCH window: disabled
[    2.038094] pci 0000:00:0a.0: setting latency timer to 64
[    2.038099] pci 0000:00:0b.0: setting latency timer to 64
[    2.038103] pci 0000:00:0c.0: setting latency timer to 64
[    2.038108] pci 0000:00:0d.0: setting latency timer to 64
[    2.038110] bus: 00 index 0 io port: [0x00-0xffff]
[    2.038112] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    2.038113] bus: 01 index 0 mmio: [0x0-0x0]
[    2.038115] bus: 01 index 1 mmio: [0xfa000000-0xfdffffff]
[    2.038116] bus: 01 index 2 mmio: [0x0-0x0]
[    2.038117] bus: 01 index 3 io port: [0x00-0xffff]
[    2.038118] bus: 01 index 4 mmio: [0x000000-0xffffffffffffffff]
[    2.038120] bus: 02 index 0 mmio: [0x0-0x0]
[    2.038121] bus: 02 index 1 mmio: [0x0-0x0]
[    2.038122] bus: 02 index 2 mmio: [0x0-0x0]
[    2.038123] bus: 02 index 3 mmio: [0x0-0x0]
[    2.038124] bus: 03 index 0 mmio: [0x0-0x0]
[    2.038125] bus: 03 index 1 mmio: [0x0-0x0]
[    2.038126] bus: 03 index 2 mmio: [0x0-0x0]
[    2.038127] bus: 03 index 3 mmio: [0x0-0x0]
[    2.038128] bus: 04 index 0 mmio: [0x0-0x0]
[    2.038129] bus: 04 index 1 mmio: [0x0-0x0]
[    2.038130] bus: 04 index 2 mmio: [0x0-0x0]
[    2.038131] bus: 04 index 3 mmio: [0x0-0x0]
[    2.038140] NET: Registered protocol family 2
[    2.072113] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    2.072655] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    2.074815] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.075418] TCP: Hash tables configured (established 262144 bind 65536)
[    2.075420] TCP reno registered
[    2.084209] NET: Registered protocol family 1
[    2.084323] checking if image is initramfs... it is
[    2.629533] Freeing initrd memory: 7811k freed
[    2.635197] audit: initializing netlink socket (disabled)
[    2.635227] type=2000 audit(1240858286.632:1): initialized
[    2.641554] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.642477] VFS: Disk quotas dquot_6.5.1
[    2.642515] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.642933] fuse init (API version 7.10)
[    2.642988] msgmni has been set to 3469
[    2.643127] alg: No test for stdrng (krng)
[    2.643134] io scheduler noop registered
[    2.643136] io scheduler anticipatory registered
[    2.643137] io scheduler deadline registered
[    2.643165] io scheduler cfq registered (default)
[    2.665510] pci 0000:00:10.0: Boot video device
[    2.773200] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    2.773229] pcieport-driver 0000:00:0b.0: found MSI capability
[    2.773249] pcieport-driver 0000:00:0b.0: irq 2303 for MSI/MSI-X
[    2.773257] pci_express 0000:00:0b.0:pcie00: allocate port service
[    2.773266] pci_express 0000:00:0b.0:pcie03: allocate port service
[    2.773304] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    2.773331] pcieport-driver 0000:00:0c.0: found MSI capability
[    2.773348] pcieport-driver 0000:00:0c.0: irq 2302 for MSI/MSI-X
[    2.773355] pci_express 0000:00:0c.0:pcie00: allocate port service
[    2.773363] pci_express 0000:00:0c.0:pcie03: allocate port service
[    2.773400] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    2.773427] pcieport-driver 0000:00:0d.0: found MSI capability
[    2.773443] pcieport-driver 0000:00:0d.0: irq 2301 for MSI/MSI-X
[    2.773451] pci_express 0000:00:0d.0cie00: allocate port service
[    2.773459] pci_express 0000:00:0d.0cie03: allocate port service
[    2.773501] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.773507] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.773619] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.773621] ACPI: Power Button (FF) [PWRF]
[    2.773658] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.773667] ACPI: Power Button (CM) [PWRB]
[    2.774137] ACPI: SSDT 6FFAE670, 0277 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[    2.774416] processor ACPI_CPU:00: registered as cooling_device0
[    2.774418] ACPI: Processor [P001] (supports 8 throttling states)
[    2.774715] ACPI: SSDT 6FFAEB00, 0277 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[    2.774965] processor ACPI_CPU:01: registered as cooling_device1
[    2.829460] ACPI Warning (nspredef-085: \_TZ_.THRM._TZD: Return Package type mismatch at index 0 - found Processor, expected Reference [20080926]
[    2.829465] ACPI: Expecting a [Reference] package element, found type C
[    2.829578] thermal LNXTHERM:01: registered as thermal_zone0
[    2.829742] ACPI: Thermal Zone [THRM] (22 C)
[    2.852282] Linux agpgart interface v0.103
[    2.852289] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.852377] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.852462] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.852650] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.852762] 00:05: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.853357] brd: module loaded
[    2.853588] loop: module loaded
[    2.853637] Fixed MDIO Bus: probed
[    2.853641] PPP generic driver version 2.4.2
[    2.853681] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.853699] Driver 'sd' needs updating - please use bus_type methods
[    2.853708] Driver 'sr' needs updating - please use bus_type methods
[    2.853742] ahci 0000:00:0e.0: version 3.0
[    2.854057] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    2.854063] ahci 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    2.854092] ahci 0000:00:0e.0: irq 2300 for MSI/MSI-X
[    2.854148] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    2.854150] ahci 0000:00:0e.0: flags: 64bit sntf led clo pmp pio 
[    2.854153] ahci 0000:00:0e.0: setting latency timer to 64
[    2.854561] scsi0 : ahci
[    2.854633] scsi1 : ahci
[    2.854677] scsi2 : ahci
[    2.854716] scsi3 : ahci
[    2.854779] ata1: SATA max UDMA/133 abar m8192@0xf9f7c000 port 0xf9f7c100 irq 2300
[    2.854781] ata2: SATA max UDMA/133 abar m8192@0xf9f7c000 port 0xf9f7c180 irq 2300
[    2.854783] ata3: SATA max UDMA/133 abar m8192@0xf9f7c000 port 0xf9f7c200 irq 2300
[    2.854785] ata4: SATA max UDMA/133 abar m8192@0xf9f7c000 port 0xf9f7c280 irq 2300
[    3.336034] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.336818] ata1.00: ATA-8: WDC WD3200AAJS-22B4A0, 01.03A01, max UDMA/133
[    3.336823] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.337716] ata1.00: configured for UDMA/133
[    4.224033] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.229780] ata2.00: ATAPI: HL-DT-ST DVDRAM GH15F, EG00, max UDMA/100
[    4.236454] ata2.00: configured for UDMA/100
[    5.232033] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.238341] ata3.00: ATA-7: SAMSUNG HD753LJ, 1AA01113, max UDMA7
[    5.238345] ata3.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.244741] ata3.00: configured for UDMA/133
[    5.564024] ata4: SATA link down (SStatus 0 SControl 300)
[    5.564160] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-2 01.0 PQ: 0 ANSI: 5
[    5.564247] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    5.564259] sd 0:0:0:0: [sda] Write Protect is off
[    5.564261] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.564279] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.564324] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    5.564334] sd 0:0:0:0: [sda] Write Protect is off
[    5.564336] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.564353] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.564355]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    5.616641] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.616678] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.619527] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH15F     EG00 PQ: 0 ANSI: 5
[    5.949133] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.949137] Uniform CD-ROM driver Revision: 3.20
[    5.949255] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.949307] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.949351] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD753LJ  1AA0 PQ: 0 ANSI: 5
[    5.949409] sd 2:0:0:0: [sdb] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    5.949419] sd 2:0:0:0: [sdb] Write Protect is off
[    5.949420] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.949438] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.949473] sd 2:0:0:0: [sdb] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    5.949483] sd 2:0:0:0: [sdb] Write Protect is off
[    5.949484] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.949501] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.949504]  sdb: [LDM] sdb1
[    6.001946] sd 2:0:0:0: [sdb] Attached SCSI disk
[    6.001978] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.002151] pata_amd 0000:00:08.0: version 0.3.10
[    6.002182] pata_amd 0000:00:08.0: setting latency timer to 64
[    6.002252] scsi4 : pata_amd
[    6.002295] scsi5 : pata_amd
[    6.003181] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    6.003183] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    6.167082] ata6: port disabled. ignoring.
[    6.167391] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    6.167706] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    6.167711] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    6.167727] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    6.167729] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    6.167776] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    6.167797] ehci_hcd 0000:00:04.1: debug port 1
[    6.167801] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    6.167813] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf9f7ec00
[    6.176041] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    6.176137] usb usb1: configuration #1 chosen from 1 choice
[    6.176179] hub 1-0:1.0: USB hub found
[    6.176189] hub 1-0:1.0: 10 ports detected
[    6.176285] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.176595] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[    6.176599] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21
[    6.176606] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    6.176608] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    6.176636] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    6.176651] ohci_hcd 0000:00:04.0: irq 21, io mem 0xf9f7f000
[    6.234038] usb usb2: configuration #1 chosen from 1 choice
[    6.234056] hub 2-0:1.0: USB hub found
[    6.234061] hub 2-0:1.0: 10 ports detected
[    6.234125] uhci_hcd: USB Universal Host Controller Interface driver
[    6.234167] usbcore: registered new interface driver libusual
[    6.234189] usbcore: registered new interface driver usbserial
[    6.234196] USB Serial support registered for generic
[    6.234204] usbcore: registered new interface driver usbserial_generic
[    6.234205] usbserial: USB Serial Driver core
[    6.234242] PNP: PS/2 Controller [PNP0303S2K,PNP0f03S2M] at 0x60,0x64 irq 1,12
[    6.234557] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.234560] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.244061] mice: PS/2 mouse device common for all mice
[    6.280095] rtc_cmos 00:08: RTC can wake from S4
[    6.280143] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    6.280180] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    6.280231] device-mapper: uevent: version 1.0.3
[    6.280294] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    6.280344] device-mapper: multipath: version 1.0.5 loaded
[    6.280346] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.280405] cpuidle: using governor ladder
[    6.280407] cpuidle: using governor menu
[    6.280703] TCP cubic registered
[    6.280746] NET: Registered protocol family 10
[    6.281036] lo: Disabled Privacy Extensions
[    6.281229] NET: Registered protocol family 17
[    6.281242] Bluetooth: L2CAP ver 2.11
[    6.281243] Bluetooth: L2CAP socket layer initialized
[    6.281245] Bluetooth: SCO (Voice Link) ver 0.6
[    6.281246] Bluetooth: SCO socket layer initialized
[    6.281269] Bluetooth: RFCOMM socket layer initialized
[    6.281273] Bluetooth: RFCOMM TTY layer initialized
[    6.281274] Bluetooth: RFCOMM ver 1.10
[    6.281846] registered taskstats version 1
[    6.281960]   Magic number: 5:266:899
[    6.282051] rtc_cmos 00:08: setting system clock to 2009-04-27 18:51:31 UTC (1240858291)
[    6.282053] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.282054] EDD information not available.
[    6.282085] Freeing unused kernel memory: 536k freed
[    6.282336] Write protecting the kernel read-only data: 6708k
[    6.312934] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    6.483320] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    6.483693] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    6.483700] forcedeth 0000:00:0f.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    6.483704] forcedeth 0000:00:0f.0: setting latency timer to 64
[    6.712032] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    6.966393] usb 1-6: configuration #1 chosen from 1 choice
[    7.003216] Initializing USB Mass Storage driver...
[    7.005066] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:21:85:03:9b:b7
[    7.005069] forcedeth 0000:00:0f.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[    7.017635] usbcore: registered new interface driver hiddev
[    7.027068] scsi6 : SCSI emulation for USB Mass Storage devices
[    7.027121] usb-storage: device found at 4
[    7.027123] usb-storage: waiting for device to settle before scanning
[    7.027136] usbcore: registered new interface driver usb-storage
[    7.027139] USB Mass Storage support registered.
[    7.083045] input: Western Digital My Book as /devices/pci0000:00/0000:00:04.1/usb1/1-6/1-6:1.1/input/input4
[    7.092102] generic-usb 0003:1058:1102.0001: input,hidraw0: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:04.1-6/input1
[    7.092125] usbcore: registered new interface driver usbhid
[    7.092128] usbhid: v2.6:USB HID core driver
[    7.190332] PM: Starting manual resume from disk
[    7.190335] PM: Resume from partition 8:5
[    7.190336] PM: Checking hibernation image.
[    7.190450] PM: Resume from disk failed.
[    7.225987] kjournald starting.  Commit interval 5 seconds
[    7.225995] EXT3-fs: mounted filesystem with ordered data mode.
[    7.440043] usb 2-3: new full speed USB device using ohci_hcd and address 2
[    7.652336] usb 2-3: configuration #1 chosen from 1 choice
[    7.956045] usb 2-5: new full speed USB device using ohci_hcd and address 3
[    8.171409] usb 2-5: configuration #1 chosen from 1 choice
[    8.460048] usb 2-10: new full speed USB device using ohci_hcd and address 4
[    8.675476] usb 2-10: configuration #1 chosen from 1 choice
[    8.678543] scsi7 : SCSI emulation for USB Mass Storage devices
[    8.678609] usb-storage: device found at 4
[    8.678610] usb-storage: waiting for device to settle before scanning
[   10.869990] udev: starting version 141
[   11.309125] Linux video capture interface: v2.00
[   11.481906] nvidia: module license 'NVIDIA' taints kernel.
[   11.724502] gspca: main v2.5.0 registered
[   11.729816] gspca: probing 041e:405f
[   11.736356] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 23
[   11.736361] nvidia 0000:00:10.0: PCI INT A -> Link[SGRU] -> GSI 23 (level, low) -> IRQ 23
[   11.736366] nvidia 0000:00:10.0: setting latency timer to 64
[   11.736771] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   11.873024] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   11.950401] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.962845] ov519: I2C synced in 0 attempt(s)
[   11.962848] ov519: starting OV7xx0 configuration
[   11.998850] ov519: Sensor is an OV7670
[   12.034965] usb-storage: device scan complete
[   12.035009] isa bounce pool size: 16 pages
[   12.080331] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   12.080746] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 19
[   12.080755] cx8800 0000:01:06.0: PCI INT A -> Link[LNKC] -> GSI 19 (level, low) -> IRQ 19
[   12.081279] cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68,autodetected], frontend(s): 2
[   12.081281] cx88[0]: TV tuner type 63, Radio tuner type -1
[   12.088649] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   12.150644] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[   12.151021] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   12.151025] HDA Intel 0000:00:09.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   12.151092] HDA Intel 0000:00:09.0: setting latency timer to 64
[   12.158869] cx2388x alsa driver version 0.0.7 loaded
[   12.202134] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
[   12.261039] tuner 0-0043: chip found @ 0x86 (cx88[0])
[   12.266316] tda9887 0-0043: creating new instance
[   12.266318] tda9887 0-0043: tda988[5/6/7] found
[   12.269165] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   12.307528] tveeprom 0-0050: Hauppauge model 69009, rev B2D3, serial# 5346646
[   12.307530] tveeprom 0-0050: MAC address is 00-0D-FE-51-95-56
[   12.307532] tveeprom 0-0050: tuner model is Philips FMD1216MEX (idx 133, type 7
[   12.307534] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   12.307536] tveeprom 0-0050: audio processor is CX882 (idx 33)
[   12.307537] tveeprom 0-0050: decoder processor is CX882 (idx 25)
[   12.307539] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
[   12.307540] cx88[0]: hauppauge eeprom: model=69009
[   12.313644] tuner-simple 0-0061: creating new instance
[   12.313646] tuner-simple 0-0061: type set to 78 (Philips FMD1216MEX MK3 Hybrid Tuner)
[   12.317672] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:0a.0/0000:01:06.0/input/input6
[   12.348143] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 19, latency: 64, mmio: 0xfd000000
[   12.357765] wm8775 0-001b: chip found @ 0x36 (cx88[0])
[   12.364237] cx88[0]/0: registered device video0 [v4l2]
[   12.364272] cx88[0]/0: registered device vbi0
[   12.364303] cx88[0]/0: registered device radio0
[   12.367975] cx88[0]/2: cx2388x 8802 Driver Manager
[   12.367989] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> Link[LNKC] -> GSI 19 (level, low) -> IRQ 19
[   12.367996] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 19, latency: 64, mmio: 0xfb000000
[   12.368495] cx88_audio 0000:01:06.1: PCI INT A -> Link[LNKC] -> GSI 19 (level, low) -> IRQ 19
[   12.368520] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   12.463559] logips2pp: Detected unknown logitech mouse model 74
[   12.500622] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   12.500625] cx88/2: registering cx8802 driver, type: dvb access: shared
[   12.500628] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68]
[   12.500630] cx88[0]/2: cx2388x based DVB/ATSC card
[   12.500631] cx8802_alloc_frontends() allocating 2 frontend(s)
[   12.535775] tuner-simple 0-0061: attaching existing instance
[   12.535778] tuner-simple 0-0061: couldn't set type to 63. Using 78 (Philips FMD1216MEX MK3 Hybrid Tuner) instead
[   12.539633] DVB: registering new adapter (cx88[0])
[   12.539636] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
[   12.539901] DVB: registering adapter 0 frontend 1 (Conexant CX22702 DVB-T)...
[   12.942902] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input7
[   13.679131] usb-storage: device scan complete
[   13.686118] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   13.693108] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   13.700123] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   13.707115] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   14.576343] gspca: probe ok
[   14.576376] usbcore: registered new interface driver ov519
[   14.576400] ov519: registered
[   14.793732] lp: driver loaded but no devices found
[   14.855291] Adding 19583192k swap on /dev/sda5.  Priority:-1 extents:1 across:19583192k
[   15.390640] EXT3 FS on sda3, internal journal
[   16.780087] type=1505 audit(1240854701.997:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2181
[   16.810248] type=1505 audit(1240854702.025:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2185
[   16.810374] type=1505 audit(1240854702.025:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2185
[   16.810405] type=1505 audit(1240854702.025:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2185
[   16.810435] type=1505 audit(1240854702.025:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2185
[   16.895949] type=1505 audit(1240854702.109:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2190
[   16.896117] type=1505 audit(1240854702.113:: operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2190
[   16.920045] type=1505 audit(1240854702.137:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2194
[   16.938972] type=1505 audit(1240854702.153:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2198
[   17.928030] usb 1-6: reset high speed USB device using ehci_hcd and address 4
[   18.624741] lirc_dev: IR Remote Control driver registered, major 61 
[   18.628035] usbcore: registered new interface driver lirc_mceusb
[   18.628040] lirc_mceusb: USB Microsoft IR Transceiver Driver v0.2
[   25.076881] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.076884] Bluetooth: BNEP filters: protocol multicast
[   25.206817] Bridge firewalling registered
[   26.025471] ppdev: user-space parallel port driver
[   26.542155] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[   26.542159] i2c-adapter i2c-0: firmware: requesting dvb-fe-cx24116.fw
[   26.602325] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[   28.304513] usb 1-6: reset high speed USB device using ehci_hcd and address 4
[   29.785065] forcedeth 0000:00:0f.0: irq 2299 for MSI/MSI-X
[   32.528065] cx24116_cmd_execute() Firmware not responding
[   32.528071] cx24116_firmware_ondemand: Writing firmware to device failed
[   32.528085] cx24116_firmware_ondemand: Firmware upload failed
[   32.528087] cx24116_cmd_execute(): Unable initialise the firmware
[   40.516060] eth0: no IPv6 routers present
[   44.704032] usb 1-6: reset high speed USB device using ehci_hcd and address 4
[   45.072029] usb 1-6: reset high speed USB device using ehci_hcd and address 4
[   55.436030] usb 1-6: reset high speed USB device using ehci_hcd and address 4
[   55.692151] scsi 6:0:0:0: Device offlined - not ready after error recovery
[   55.702010] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   55.702081] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   55.713231] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[   55.714121] sd 7:0:0:1: Attached scsi generic sg4 type 0
[   55.734997] sd 7:0:0:2: [sde] Attached SCSI removable disk
[   55.735069] sd 7:0:0:2: Attached scsi generic sg5 type 0
[   55.813268] sd 7:0:0:3: [sdf] Attached SCSI removable disk
[   55.814429] sd 7:0:0:3: Attached scsi generic sg6 type 0

Grateful for any help which would stop me reverting to Windows. Should I go back to Intrepid? etc

:(

---

### Post by pyroxer on 2009-04-27
Which firmware are you using?  There's various different ones on linuxtv 
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000)

I'm not at the PC now so can't check my setup, but I just quickly tried whatever the firmware was that was installed by jaunty.  It's a new build pc with a new card so I haven't yet tried intrepid etc but I'll have a go later and report back.

---

### Post by viv2 on 2009-04-27
Thanks for the querry

I have used the latest as per these instructions
wget [http://tevii.com/Tevii_linuxdriver_0815.rar](http://tevii.com/Tevii_linuxdriver_0815.rar)
sudo apt-get install unrar-free
unrar x Tevii_linuxdriver_0815.rar
sudo cp tevii_linuxdriver_0815/fw/dvb-fe-cx24116.fw /lib/firmware/dvb-fe-cx24116-1.23.86.1.fw
sudo ln -s /lib/firmware/dvb-fe-cx24116-1.23.86.1.fw /lib/firmware/dvb-fe-cx24116.fw

Did you not need to get this firmware as it is now distributed as part of Jaunty?
I suspect I should have not done this either

hg clone [http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/)
 cd v4l-dvb
 make
 make install
 reboot

As you can see I have done a lot of straw clutching!

---

### Post by vinalopo on 2009-04-27
Personally have tried both with both without the latest firmware but no success
In my case too it's a new built htpc so I haven't tried the card in the past

---

### Post by pyroxer on 2009-04-27
yep, jaunty has added a firmware.  Not sure which version it is tho.

[http://packages.ubuntu.com/search?searchon=contents&keywords=dvb-fe-cx24116.fw&mode=exactfilename&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=dvb-fe-cx24116.fw&mode=exactfilename&suite=jaunty&arch=any)

---

### Post by viv2 on 2009-04-27
Unlinked the previous firmware which deleted it so reinstalled linux-firmware but it is still not uploaded. Not sure how to reverse the install of v4l-dvb if that is also unnecessary. 

My lsmod output is now

Module                  Size  Used by
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
lirc_mceusb            18080  0 
lirc_dev               22088  1 lirc_mceusb
input_polldev          12688  0 
video                  29204  0 
output                 11648  1 video
nfsd                  285344  17 
auth_rpcgss            52512  1 nfsd
exportfs               13440  1 nfsd
nfs                   304464  0 
lockd                  83796  2 nfsd,nfs
nfs_acl                11776  2 nfsd,nfs
sunrpc                227304  15 nfsd,auth_rpcgss,nfs,lockd,nfs_acl
lp                     19588  0 
parport                49584  2 ppdev,lp
cx22702                15108  1 
isl6421                10496  1 
cx24116                25608  1 
cx88_dvb               31748  1 
cx88_vp3054_i2c        11264  1 cx88_dvb
videobuf_dvb           16388  1 cx88_dvb
dvb_core              109484  2 cx88_dvb,videobuf_dvb
wm8775                 12888  1 
tuner_simple           23956  2 
tuner_types            26240  1 tuner_simple
tda9887                19588  1 
tda8290                23816  0 
tuner                  33776  2 
snd_hda_intel         557364  0 
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
cx88_alsa              21128  0 
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                99336  3 snd_hda_intel,cx88_alsa,snd_pcm_oss
cx8802                 26116  1 cx88_dvb
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cx8800                 45972  0 
snd_timer              34064  2 snd_seq,snd_pcm
cx88xx                 91820  4 cx88_dvb,cx88_alsa,cx8802,cx8800
ir_common              60292  1 cx88xx
i2c_algo_bit           15364  2 cx88_vp3054_i2c,cx88xx
snd                    78792  10 snd_hda_intel,snd_seq_oss,snd_rawmidi,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_seq_device,snd_timer
tveeprom               23556  1 cx88xx
nvidia               8123768  26 
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
v4l2_common            26880  4 wm8775,tuner,cx8800,cx88xx
videobuf_dma_sg        22660  5 cx88_dvb,cx88_alsa,cx8802,cx8800,cx88xx
btcx_risc              13960  4 cx88_alsa,cx8802,cx8800,cx88xx
videobuf_core          29572  5 videobuf_dvb,cx8802,cx8800,cx88xx,videobuf_dma_sg
psmouse                64028  0 
gspca_ov519            24964  0 
pcspkr                 11136  0 
serio_raw              14468  0 
gspca_main             34816  1 gspca_ov519
videodev               49440  6 wm8775,tuner,cx8800,cx88xx,v4l2_common,gspca_main
v4l1_compat            24068  1 videodev
v4l2_compat_ioctl32    19712  1 videodev
usbhid                 47040  0 
usb_storage            94912  0 
forcedeth              68368  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
root@acer:~# 

Thanks again.

---

### Post by viv2 on 2009-04-28
Perhaps it is a Jaunty bug. Has anyone got the HVR4000 to work with Jaunty or does it still work after an upgrade? Perhaps I should revert to 8:10. (originally posted to x64 forum in error)

---

### Post by Neon Dusk on 2009-04-28
Just had this problem myself with a clean Jaunty x64 install.

The dvb-fe-cx24116.fw firmware file supplied with Jaunty has a md5sum of 9950fe612d47217e6068f7141de225b0. I've replaced with a different firmware file that has a md5sum of 417cafd3b10e207e1dba9a03ad63e405 which seems to work ok.

I got the firmware from
```

wget ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip
unzip -jo 88x_2_119_25023_WHQL.zip Driver88/hcw88bda.sys
dd if=hcw88bda.sys of=/lib/firmware/dvb-fe-cx24116.fw skip=81768 bs=1 count=32522

```

Edit: This was using a Nova HD S2 card (detected as Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1)

---

### Post by pyroxer on 2009-04-28
@neon dusk : just retried with the firmware you posted, all seems to be OK now.  Nice one!

Looks like jaunty has a broken firmware.

thanks!

---

### Post by viv2 on 2009-04-30
Well done. Losing patience I reinstalled 8:10 and that now works. I have just got to get one of Kaffeine, M-player or xine working easily! Kaffine scans the channels nicely  but HD seems  a  problem in both xine (no picture) and Kaffeine (juddery play). I have tried mythtv but have never got it to do anything TV wise or anything else as all my media is off the ubuntu drive and I can't seem to configure the sources! Certainly not with smb4k.

Does the jaunty firmware problem get back to Canonical by virtue of these exchanges?

---

### Post by Neon Dusk on 2009-05-02
> **viv2 said:**
> 

Does the jaunty firmware problem get back to Canonical by virtue of these exchanges?

It's been reported on [launchpad](https://bugs.launchpad.net/mythbuntu/+bug/363682/) so will hopefully get fixed in a new linux-firmware version.

---

### Post by bradders123 on 2009-05-04
worked fot me after a week of messing about following all different instructions, well it scans for channels in kaffiene, if i can get it to work with wythtv is the next problem....

---

