---
title: "Aborted Back To Back Recordings"
date: 2008-01-18
forum: Mythbuntu
---

### Post by jwbrown77 on 2008-01-18
I recently setup a Mythbuntu 7.1 installation and almost everything is working correctly.  However, the second recording in back to back scheduled recordings gets aborted and I can't figure out why.

Here's some background on my hardware:

Mythbuntu 7.1
Hauppauge PVR-150
External Digital Cable Box controlled over the serial port with changechannel.py (the compiled c binary didn't work)

Included below is the output from mythbackend.log.  I'm including both the first (successful) recording as well as the aborted recording.

2008-01-13 18:29:29.723 TVRec(1): ASK_RECORDING 1 29 0
**2008-01-13 18:30:02.852 Started recording: At the Movies With Ebert & Roeper: channel 1007 on cardid 1, sourceid 1**
2008-01-13 18:30:03.887 ret_pid(0) child(19679) status(0x0)
2008-01-13 18:30:04.890 ret_pid(0) child(19679) status(0x0)
2008-01-13 18:30:05.897 ret_pid(19679) child(19679) status(0x0)
2008-01-13 18:30:05.901 External Tuning program exited with no error
2008-01-13 18:30:05.965 Finished recording Superman "Father's Day": channel 1341
2008-01-13 18:30:06.247 Finished recording Superman "Father's Day": channel 1341
0: start_time: 2986.071 duration: 161.976
1: start_time: 2986.042 duration: 161.981
stream: start_time: 33178.243 duration: 1800.057 bitrate=5191 kb/s
2008-01-13 18:30:06.317 AFD: Opened codec 0x82c5cb0, id(MPEG2VIDEO) type(Video)
2008-01-13 18:30:06.324 AFD: Opened codec 0x82c70d0, id(MP2) type(Audio)
2008-01-13 18:30:06.462 TVRec(1): RingBufferChanged()
2008-01-13 18:30:06.481 Finished recording Superman "Father's Day": channel 1341
2008-01-13 18:31:14.204 Expiring Superman "Ghost in the Machine" from Sat Jan 12 18:00:00 2008, 1113 MBytes, forced expire (LiveTV recording)
2008-01-13 18:59:29.086 TVRec(1): ASK_RECORDING 1 29 1
2008-01-13 19:00:00.118 TVRec(1): Enabling Full LiveTV UI.
**2008-01-13 19:00:02.246 Finished recording At the Movies With Ebert & Roeper: channel 1007** *(My Note: This recorded correctly)*
2008-01-13 19:00:02.338 TVRec(1): Enabling Full LiveTV UI.
0: start_time: 3148.146 duration: 161.928
1: start_time: 3148.094 duration: 161.965
stream: start_time: 34978.819 duration: 1799.779 bitrate=5187 kb/s
2008-01-13 19:00:02.377 AFD: Opened codec 0x8228c00, id(MPEG2VIDEO) type(Video)
**2008-01-13 19:00:02.417 Canceled recording (Aborted): 60 Minutes: channel 1002 on cardid 1, sourceid 1**
2008-01-13 19:00:02.422 AFD: Opened codec 0x831a650, id(MP2) type(Audio)
2008-01-13 19:00:02.425 TVRec(1): RingBufferChanged()
2008-01-13 19:00:02.520 Finished recording At the Movies With Ebert & Roeper: channel 1007
2008-01-13 19:00:03.432 Reschedule requested for id 0.
2008-01-13 19:00:04.723 Scheduled 340 items in 1.3 = 0.01 match + 1.29 place
**2008-01-13 19:00:04.730 Canceled recording (Aborted): 60 Minutes: channel 1002 on cardid 1, sourceid 1**
2008-01-13 19:01:14.273 Expiring Batman "Eternal Youth" from Sat Jan 12 18:30:00 2008, 1113 MBytes, forced expire (LiveTV recording)
[mpeg2video @ 0xb72f8ce8]Warning MVs not available

----------------

It says LiveTV, but these were scheduled in the menu.

Recordings only abort under these conditions.  Regular recordings (not back to back) always work.

I saw a post from last year with a person that had the same problem, but no resolution was ever posted for it.  I'm wondering if anyone else has had this problem and found a solution?

If more info is needed, please let me know and I will provide.  TIA.

---

### Post by haggiscanvas on 2008-01-18
Not that it helps, but I am having the same problem...

---

### Post by jwbrown77 on 2008-01-18
No, it helps.  I know I'm not using some obscure configuration somewhere that no one else can duplicate.  :)

---

### Post by jwbrown77 on 2008-01-18
Oh, one more thing...

The recording that's aborted still shows up in the LiveTV recordings.  I tried to uncheck the "Auto-Expire" box in MythWeb to keep the recording longer than the default expiration time (1 day) but the recording still gets erased.

---

### Post by jwbrown77 on 2008-01-19
One more update...

I tried what was suggested in the thread from last year: Making sure I'm not in LiveTV when the recordings are scheduled to start, and that does seem to work.

I wouldn't call this a "fix" but it's a workaround.  I'd still be curious to know how to make it work in case I forget and leave it in livetv mode.

---

