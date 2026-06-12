---
title: "&quot;Error opening jump programme file&quot; on DVB/Radio channel change."
date: 2013-01-06
forum: Mythbuntu
---

### Post by os2 on 2013-01-06
Radio channels don't work. I get this error instead when starting or switching to a Radio channel on a DVB MUX.

The TV channels play fine in the FE.

Here is fragment verbose from mythbackend.

I bring to attention the error highlighted in Red. The other errors, I get them anyway and TV still works.

Am I missing a component or setting?

> en demux device /dev/dvb/adapter0/demux0 for filter on pid 0x0
2013-01-06 12:17:27.669565 E  PIDInfo(/dev/dvb/adapter0/frontend0): Failed to open demux device /dev/dvb/adapter0/demux0 for filter on pid 0x1010
2013-01-06 12:17:28.123402 I  TVRec(2): Changing from WatchingLiveTV to None
2013-01-06 12:17:28.220384 I  TVRec(2): FinishedRecording(5176_2013-01-06T11:17:17Z) damaged recq:<RecordingQuality overall_score="0" key="5176_2013-01-06T11:17:17Z" countinuity_error_count="0" packet_count="1613">
    <Gap start="2013-01-06T11:17:16Z" end="2013-01-06T11:30:00Z" duration="763" />
</RecordingQuality>

2013-01-06 12:17:28.230051 I  MainServer::ANN Playback
2013-01-06 12:17:28.230059 I  adding: linux-2xmk.site as a client (events: 0)
[COLOR=Red]2013-01-06 12:17:28.231411 E  MainServer::HandleRecorderQuery() Unknown encoder: 1[/COLOR]
2013-01-06 12:17:28.246966 I  TVRec(2): Changing from None to WatchingLiveTV
2013-01-06 12:17:28.249498 I  TVRec(2): HW Tuner: 2->2
2013-01-06 12:17:28.255856 W  DVBChan(2:/dev/dvb/adapter0/frontend0): 'Auto' bandwidth parameter unsupported by this driver.
2013-01-06 12:17:28.259440 N  AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2013-01-06 12:17:28.302724 I  TVRec(2): Changing from WatchingLiveTV to None
2013-01-06 12:17:28.347388 E  PIDInfo(/dev/dvb/adapter0/frontend0): Failed to open demux device /dev/dvb/adapter0/demux0 for filter on pid 0x1023
2013-01-06 12:17:28.347428 E  PIDInfo(/dev/dvb/adapter0/frontend0): Failed to open demux device /dev/dvb/adapter0/demux0 for filter on pid 0x0


---

### Post by os2 on 2013-01-06
Screenshot.

---

