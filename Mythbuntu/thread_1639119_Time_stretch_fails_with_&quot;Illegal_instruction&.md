---
title: "Time stretch fails with &quot;Illegal instruction&quot; in 0.24"
date: 2010-12-06
forum: Mythbuntu
---

### Post by Quadari on 2010-12-06
Hi All,

I recently upgraded my mhthtv from 0.23 to 0.24.  In 0.23 the "time strech" feature worked flawlessly on my mythbuntu box.                         However, with 0.24 when I choose "time stretch" the mythfrontend just crashes immediately.  I get the error (in the terminal) "Illegal instruction".  Without much else helpful. 

Included below is the output in the terminal for the second when I click the "Adjust Time Stretch" key and it quits.  I've tried both stretching up (to 1.1x) and stretching down (to 0.9x) and get the same result.

Anyone know if this is a known bug in 0.24?   It's running on a mythbuntu box using Ubuntu 10.04.1 LTS.

Thanks.

```

2010-12-06 11:21:22.893 WriteAudio: Preparing 4096 bytes (512 frames)
2010-12-06 11:21:22.893 AO: GetAudiotime audt=87655851 atc=87656900 mb=339968 sb=63056 tb=403024 sr=48000 obpf=8 bpf=8 sf=1 40302400000 1049
2010-12-06 11:21:22.893 WriteAudio: Preparing 4096 bytes (512 frames)
2010-12-06 11:21:22.908 AVSync show
2010-12-06 11:21:22.908 AO: GetAudiotime audt=87655866 atc=87656900 mb=339968 sb=57200 tb=397168 sr=48000 obpf=8 bpf=8 sf=1 39716800000 1034
2010-12-06 11:21:22.908 A/V timecodes audio 87655866 video 87655829 frameinterval 33366 avdel -37 avg -37473 tcoffset 0
2010-12-06 11:21:22.910 TV: OSDDialogEvent: result 3 text 0.9X action ADJUSTSTRETCH0.9
2010-12-06 11:21:22.910 Player(0): Play(  0.9, normal 1, unpause audio 1)
2010-12-06 11:21:22.911 AO: Pause 0
2010-12-06 11:21:22.911 ###   87656930 15 3 2 42 0   8 -
2010-12-06 11:21:22.912   87656930 '
2010-12-06 11:21:22.912 ck
2010-12-06 11:21:22.912 ###   87656930 15 3 2  2 0   8 -
2010-12-06 11:21:22.912   87656930 '
2010-12-06 11:21:22.912 ck
2010-12-06 11:21:22.912 AFD: video timecode 7889114776 7889123785 7889114776 87656830 87656797
2010-12-06 11:21:22.912 AO: GetAudiotime audt=87655870 atc=87656900 mb=335872 sb=59760 tb=395632 sr=48000 obpf=8 bpf=8 sf=1 39563200000 1030
2010-12-06 11:21:22.913 WriteAudio: Preparing 4096 bytes (512 frames)
2010-12-06 11:21:22.913 AO: GetAudiotime audt=87655871 atc=87656900 mb=331776 sb=63600 tb=395376 sr=48000 obpf=8 bpf=8 sf=1 39537600000 1029
2010-12-06 11:21:22.913 WriteAudio: Preparing 4096 bytes (512 frames)
2010-12-06 11:21:22.913 AFD: audio timecode 7889121001 7889121001 87656900 87656932
2010-12-06 11:21:22.913 AO: AddFrames frames=1536, bytes=6144, used=331777, free=2740223, timecode=87656900 needsupmix=0
2010-12-06 11:21:22.913 AO: SetAudiotime atc=87656932 tc=87656900 f=1536 pfu=0 pfs=0
2010-12-06 11:21:22.914 UpdateOSDSeekMessage(Play 0.9x, 2)
2010-12-06 11:21:22.933 AO: GetAudiotime audt=87655892 atc=87656932 mb=339968 sb=59768 tb=399736 sr=48000 obpf=8 bpf=8 sf=1 39973600000 1040
2010-12-06 11:21:22.934 WriteAudio: Preparing 4096 bytes (512 frames)
2010-12-06 11:21:22.934 AO: GetAudiotime audt=87655892 atc=87656932 mb=335872 sb=63672 tb=399544 sr=48000 obpf=8 bpf=8 sf=1 39954400000 1040
2010-12-06 11:21:22.934 WriteAudio: Preparing 4096 bytes (512 frames)
2010-12-06 11:21:22.939 Player(0): Play speed: rate: 29.97 speed: 0.9 skip: 1 => new interval 37074
2010-12-06 11:21:22.939 VDP: LoadBestPreferences(528x480, 26.973)
2010-12-06 11:21:22.939 AO: Using time stretch 0.9
2010-12-06 11:21:22.940 Player(0): Stretch Factor 0.9, disable passthru 
2010-12-06 11:21:22.940 AFD: Disabling pass through
2010-12-06 11:21:22.940 Player(0): Disabled deinterlacing
2010-12-06 11:21:22.940 AO: GetAudiotime audt=87656002 atc=87656932 mb=335872 sb=61280 tb=397152 sr=48000 obpf=8 bpf=8 sf=0.9 35743680000 930
2010-12-06 11:21:22.955 AO: GetAudiotime audt=87656015 atc=87656932 mb=331776 sb=59768 tb=391544 sr=48000 obpf=8 bpf=8 sf=0.9 35238960000 917
2010-12-06 11:21:22.955 WriteAudio: Preparing 4096 bytes (512 frames)
2010-12-06 11:21:22.955 AO: GetAudiotime audt=87656015 atc=87656932 mb=327680 sb=63704 tb=391384 sr=48000 obpf=8 bpf=8 sf=0.9 35224560000 917
2010-12-06 11:21:22.955 WriteAudio: Preparing 4096 bytes (512 frames)
2010-12-06 11:21:22.974 AVSync waitforframe 0 0
2010-12-06 11:21:22.974 AVSync show
2010-12-06 11:21:22.975 AO: GetAudiotime audt=87656033 atc=87656932 mb=327680 sb=56176 tb=383856 sr=48000 obpf=8 bpf=8 sf=0.9 34547040000 899
2010-12-06 11:21:22.975 A/V timecodes audio 87656033 video 87655863 frameinterval 37074 avdel -170 avg -37354 tcoffset 0
2010-12-06 11:21:22.975 AO: GetAudiotime audt=87656033 atc=87656932 mb=327680 sb=56000 tb=383680 sr=48000 obpf=8 bpf=8 sf=0.9 34531200000 899
2010-12-06 11:21:22.976 AO: GetAudiotime audt=87656034 atc=87656932 mb=323584 sb=59776 tb=383360 sr=48000 obpf=8 bpf=8 sf=0.9 34502400000 898
2010-12-06 11:21:22.976 WriteAudio: Preparing 4096 bytes (512 frames)
2010-12-06 11:21:22.978 ###   87656864 15 3 2 42 0   8 -
2010-12-06 11:21:22.978   87656864 '
2010-12-06 11:21:22.978  B
2010-12-06 11:21:22.978 ###   87656864 15 3 2  2 0   8 -
2010-12-06 11:21:22.979   87656864 '
2010-12-06 11:21:22.979  B
2010-12-06 11:21:22.979 AFD: video timecode 7889117779 7889117779 7889117779 87656864 87656830
2010-12-06 11:21:22.979 RingBuf(/var/lib/mythtv/recordings/2112_20101205150000.mpg): ReadPriv(..32768, normal) @491520 -- begin
2010-12-06 11:21:22.979 RingBuf(/var/lib/mythtv/recordings/2112_20101205150000.mpg): ReadPriv(..32768, normal) -- copying data
2010-12-06 11:21:22.979 RingBuf(/var/lib/mythtv/recordings/2112_20101205150000.mpg): ReadPriv(..32768, normal) -- checksum 16481
2010-12-06 11:21:22.976 AO: GetAudiotime audt=87656034 atc=87656932 mb=319488 sb=63768 tb=383256 sr=48000 obpf=8 bpf=8 sf=0.9 34493040000 898
2010-12-06 11:21:22.981 WriteAudio: Preparing 4096 bytes (512 frames)
2010-12-06 11:21:22.981 RingBuf(/var/lib/mythtv/recordings/2112_20101205150000.mpg): safe_read(...@0, 491520) -- begin
2010-12-06 11:21:22.982 RingBuf(/var/lib/mythtv/recordings/2112_20101205150000.mpg): safe_read(...@0, 491520) -> 491520
2010-12-06 11:21:22.982 RingBuf(/var/lib/mythtv/recordings/2112_20101205150000.mpg): rbwpos += 480K requested 480K in read
2010-12-06 11:21:22.983 RingBuf(/var/lib/mythtv/recordings/2112_20101205150000.mpg): @ end of read ahead loop
2010-12-06 11:21:22.987 AFD: audio timecode 7889123881 7889123881 87656932 87656964
2010-12-06 11:21:22.987 AO: AddFrames frames=1536, bytes=6144, used=319489, free=2752511, timecode=87656932 needsupmix=0
2010-12-06 11:21:22.987 AO: SetAudiotime atc=87656944 tc=87656932 f=1536 pfu=-960 pfs=0
2010-12-06 11:21:22.988 AVSync waitforframe -16662 0
2010-12-06 11:21:22.988 AVSync show
2010-12-06 11:21:22.989 AO: GetAudiotime audt=87656057 atc=87656944 mb=319488 sb=59104 tb=378592 sr=48000 obpf=8 bpf=8 sf=0.9 34073280000 887
2010-12-06 11:21:22.989 A/V timecodes audio 87656057 video 87655896 frameinterval 37074 avdel -161 avg -70515 tcoffset 0
2010-12-06 11:21:22.989 AO: GetAudiotime audt=87656058 atc=87656944 mb=319488 sb=58944 tb=378432 sr=48000 obpf=8 bpf=8 sf=0.9 34058880000 886
2010-12-06 11:21:22.990 ###   87656897 15 3 2 42 0   8 -
2010-12-06 11:21:22.990   87656897 '
2010-12-06 11:21:22.990 is
2010-12-06 11:21:22.991 ###   87656897 15 3 2  2 0   8 -
2010-12-06 11:21:22.992   87656897 '
2010-12-06 11:21:22.992 is
2010-12-06 11:21:22.992 AFD: video timecode 7889120782 7889120782 7889120782 87656897 87656864
2010-12-06 11:21:22.992 AFD: audio timecode 7889126761 7889126761 87656964 87656996
2010-12-06 11:21:22.992 AO: AddFrames frames=1536, bytes=6144, used=319489, free=2752511, timecode=87656964 needsupmix=0
Illegal instruction

```

---

