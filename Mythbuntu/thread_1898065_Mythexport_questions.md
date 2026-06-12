---
title: "Mythexport questions"
date: 2011-12-20
forum: Mythbuntu
---

### Post by williammanda on 2011-12-20
I'm having a little trouble getting a video to play correctly and I am a novice. The two results I'm getting are:
1. Audio lagging video by .5 - 1 sec using the mepg4 codec.
2. Video freezing after playing but audio continues correctly using the H264 codec. 

Here is what I'm using:

LG LS670 phone - MSM7627 processer, display 480*320 16M, android ver 2.3
Video player - Moboplayer and the standard player with android
Video format - mp4
The following pm files:

Homebrewmpeg4.pm
```
#!/usr/bin/perl 

# Update this with a package name relivant to your new config.
package Homebrewmpeg4;

use ExportBase;

our @ISA = qw(ExportBase);

#Example strings, replace with something relivant to your new config.
my $description = "Low Resolution (480x320) Portable MPEG4 Settings.";
my $devices = "My LG Phone";
my $notes = "12-19-11";
my $version = "1.0";

sub new{
    my $class = shift;
    my $self = $class->SUPER::new(shift, shift, $description, $devices, $notes, $version);
    bless $self, $class;
    return $self;
}

sub export{
    my( $self ) = @_;

    # Any command can go here, below is an example of ffmpeg, but you can use anything you would like.
    # Available variables are inputFile, outputFile, and extension
    # system("ffmpeg -i \'$self->{_inputFile}\' -y -acodec libfaac -ab 64kb -ar 22050 -ac 2 -vcodec mpeg4 -b 384kb -r 25 -s 480x320 -aspect 16:9 \'$self->{_outputFile}$self->{_extension}\'");
    system("ffmpeg -i \'$self->{_inputFile}\' -y -acodec libmp3lame -vcodec mpeg4 -b 384kb -s 480x320 -ac 2 \'$self->{_outputFile}$self->{_extension}\'");
}

1;
```

Homebrewh264.pm
```
#!/usr/bin/perl 

# Update this with a package name relivant to your new config.
package Homebrewh264;

use ExportBase;

our @ISA = qw(ExportBase);

#Example strings, replace with something relivant to your new config.
my $description = "Low Resolution (480x320) Portable H264 Settings.";
my $devices = "My LG Phone";
my $notes = "12-19-11";
my $version = "1.0";

sub new{
    my $class = shift;
    my $self = $class->SUPER::new(shift, shift, $description, $devices, $notes, $version);
    bless $self, $class;
    return $self;
}

sub export{
    my( $self ) = @_;

    # Any command can go here, below is an example of ffmpeg, but you can use anything you would like.
    # Available variables are inputFile, outputFile, and extension
    system("ffmpeg -i \'$self->{_inputFile}\' -y -s 480x320 -b 384k -vcodec libx264 -flags +loop+mv4 -cmp 256 -partitions +parti4x4+parti8x8+partp4x4+partp8x8+partb8x8 -subq 7 -trellis 1 -refs 5 -bf 0 -flags2 +mixed_refs -coder 0 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -qmin 10 -qmax 51 -qdiff 4 -acodec libfaac -ac 2 -r 30 \'$self->{_outputFile}$self->{_extension}\'");
}

1;
```

PortableH264LowRes.pm
```
#!/usr/bin/perl 

package PortableH264LowRes;

use ExportBase;

our @ISA = qw(ExportBase);

my $description = "Low Resolution (480x320) Portable H264 Settings.";
my $devices = "Low Resolution Android Devices (example HTC Hero), iPod Classic, iPod Nano";
my $notes = "Requires AAC, <a href=\"https://help.ubuntu.com/community/Medibuntu\">activate Medibuntu</a>";
my $version = "1.0";

sub new{
    my $class = shift;
    my $self = $class->SUPER::new(shift, shift, $description, $devices, $notes, $version);
    bless $self, $class;
    return $self;
}

sub export{
    my( $self ) = @_;

    #system("ffmpeg -i \'$self->{_inputFile}\' -y -pass 1 -an -vcodec libx264 -vpre slowfirstpass -vpre ipod320 -b 1500kb -bt 1000kb -threads 0 -s 480x320 -aspect 16:9 -f ipod \'$self->{_outputFile}$self->{_extension}\' && ffmpeg -i \'$self->{_inputFile}\' -y -pass 2 -vcodec libx264 -vpre hq -vpre ipod320 -b 1500kb -bt 1000kb -threads 0 -s 480x320 -acodec libfaac -ab 192kb -ac 2 -aspect 16:9 -f ipod \'$self->{_outputFile}$self->{_extension}\'");

    system("ffmpeg -i \'$self->{_inputFile}\' -y -pass 1 -an -vcodec libx264 -vpre slowfirstpass -vpre ipod320 -b 384kb -threads 0 -s 480x320 -aspect 16:9 -f ipod \'$self->{_outputFile}$self->{_extension}\' && ffmpeg -i \'$self->{_inputFile}\' -y -pass 2 -vcodec libx264 -vpre hq -vpre ipod320 -b 384kb -threads 0 -s 480x320 -acodec libfaac -ar 22050 -ac 2 -aspect 16:9 -f ipod \'$self->{_outputFile}$self->{_extension}\'");

}

1;
```

Following is the the log of some of the trials

```
Stream #0.0: Video: mpeg4 (hq), yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 800 kb/s, 60k tbn, 59.94 tbc
Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, 2 channels, s16, 110 kb/s

Low Res result - video freezing after 5 seconds and audio is off. ELR Maries Meatballs
Stream #0.0: Video: mpeg4 (hq), yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 600 kb/s, 60k tbn, 59.94 tbc
Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, 2 channels, s16, 32 kb/s

Homebrew result - video works, not bad but audio still lags 1 sec, ELR displine
Stream #0.0: Video: mpeg4, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 384 kb/s, 25 tbn, 25 tbc
Stream #0.1(eng): Audio: libmp3lame, 22050 Hz, 2 channels, s16, 64 kb/s

Homebrew change - acodec to libfaac. Result - video and audio still the same ELR 1st 6 yrs
Stream #0.0: Video: mpeg4, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 384 kb/s, 25 tbn, 25 tbc
Stream #0.1(eng): Audio: libfaac, 22050 Hz, 2 channels, s16, 64 kb/s

Homebrew change - only included video and audio codec and video size. Result - Video and audio were bad but the video played. ELR Meet the parents
Stream #0.0: Video: mpeg4, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 200 kb/s, 60k tbn, 59.94 tbc
Stream #0.1(eng): Audio: libfaac, 48000 Hz, 5.1, s16, 64 kb/s

Homebrew change - included video and audio codec, video bit rate 500, video size and 2 channels. Result - The video was worse and still stopped every 2 or 3 minutes, also the audio still lagged. ELR The Plan
Stream #0.0: Video: mpeg4, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 500 kb/s, 60k tbn, 59.94 tbc
Stream #0.1(eng): Audio: libfaac, 48000 Hz, 2 channels, s16, 64 kb/s

Homebrew change - included video and audio codec, video bit rate 480, video size and 2 channels. Result - The video was bad and it stopped every second. The audio still lagged. ELR Sleepover at Peggys
Stream #0.0: Video: mpeg4, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 480 kb/s, 60k tbn, 59.94 tbc
Stream #0.1(eng): Audio: libfaac, 48000 Hz, 2 channels, s16, 64 kb/s

Homebrew change - Changed back to libmp3lame and 384 video bit rate. Result - The video was better but would freeze after 5 minutes and the audio lag was better. ELR Whos Next
Stream #0.0: Video: mpeg4, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 384 kb/s, 60k tbn, 59.94 tbc
Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, 2 channels, s16, 64 kb/s

Homebrew change - Changed to H264 video codec w/ 384 bit rate and libfaac audio codec. Result - Video seemed ok but had bad audio sound and lagged. ELR The Shower
Stream #0.0: Video: libx264, yuv420p, 432x320 [PAR 187:142 DAR 5049:2840], q=10-51, 384 kb/s, 15 tbn, 15 tbc
Stream #0.1(eng): Audio: libfaac, 48000 Hz, 5.1, s16, 64 kb/s

Homebrew change - Changed the video size to 480-320 and added 2 channel. Result - The video seems play fine but still a small lad in audio. ELR The Shower
Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, 384 kb/s, 15 tbn, 15 tbc
Stream #0.1(eng): Audio: libfaac, 48000 Hz, 2 channels, s16, 64 kb/s

Homebrew change - Changed the fps to 30 from 15. Result - The video was good  but still a small lad in audio. ELR The_Bachelor_Party
Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, 384 kb/s, 30 tbn, 30 tbc
Stream #0.1(eng): Audio: libfaac, 48000 Hz, 2 channels, s16, 64 kb/s

Portable H264 Low Res - Changed video bit rate to 384 and removed bt and ab. Result - The video and audio were great but the video would freeze after 20 sec. ELR Fun w/ Debra.
Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, pass 1, 384 kb/s, 60k tbn, 59.94 tbc
Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, pass 2, 384 kb/s, 60k tbn, 59.94 tbc
Stream #0.1(eng): Audio: libfaac, 48000 Hz, 2 channels, s16, 64 kb/s

Portable H264 Low Res - Changed video bit rate to 288. Result - The video and audio were the same but the video would freeze after 10 sec. ELR Roberts Wedding.
Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, pass 1, 288 kb/s, 60k tbn, 59.94 tbc
Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, pass 2, 288 kb/s, 60k tbn, 59.94 tbc
Stream #0.1(eng): Audio: libfaac, 48000 Hz, 2 channels, s16, 64 kb/s

Portable H264 Low Res - Changed video bit rate to 480. Result - No change. ELR Fun w/ Debra.
Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, pass 1, 480 kb/s, 60k tbn, 59.94 tbc

Portable H264 Low Res - Changed video bit rate to 384 and audio freq to 22050. Result -  The recording plays fine except for the video freezing after 10 sec. ELR Fun w/ Debra.
Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, pass 1, 384 kb/s, 60k tbn, 59.94 tbc
Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, pass 2, 384 kb/s, 60k tbn, 59.94 tbc
Stream #0.1(eng): Audio: libfaac, 22050 Hz, 2 channels, s16, 64 kb/s

```

Using the android sdk platform tools, the following is the last logcat (./adb logcat) snapshot of the video playing until the video freezes:

```
V/AudioHardwareMSM72XX( 1389): open driver
V/AudioHardwareMSM72XX( 1389): get config
V/AudioHardwareMSM72XX( 1389): set config
V/AudioHardwareMSM72XX( 1389): buffer_size: 4800
V/AudioHardwareMSM72XX( 1389): buffer_count: 2
V/AudioHardwareMSM72XX( 1389): channel_count: 2
V/AudioHardwareMSM72XX( 1389): sample_rate: 44100
W/ciq     ( 1966): browserCallEvent() EVENT_DATA_RCV_FINISH - Invalid sequence
I/ActivityManager( 1457): Starting: Intent { act=android.intent.action.VIEW dat=http://192.168.1.100/mythexport/video/WNABDT-Everybody_Loves_Raymond-Fun_With_Debra-2011121202000.mp4 typ=video/mp4 cmp=com.clov4r.android.nil/.MainActivity } from pid 1966
V/mytag   ( 2125): onCreate
V/tag     ( 2125): currentPlayMode=false
V/item    ( 2125): read  success!
V/item    ( 2125): read file success!
V/item    ( 2125): read  success!
I/ActivityManager( 1457): Starting: Intent { cmp=com.clov4r.android.nil/.SystemPlayer (has extras) } from pid 2125
W/AudioFlinger( 1389): write blocked for 230 msecs, 10 delayed writes, thread 0xcc08
W/Resources( 2125): Converting to string: TypedValue{t=0x12/d=0x0 a=3 r=0x7f090023}
W/drawable( 2125): Bad element under <shape>: background
V/item    ( 2125): read file success!
W/Resources( 2125): Converting to string: TypedValue{t=0x12/d=0x0 a=3 r=0x7f090023}
W/ciq     ( 1966): browserCallEvent() EVENT_PAGE_RENDER_FINISH - Invalid sequence
I/dun_service( 1663): process rmnet event
I/dun_service( 1663): Post event 3
E/dun_service( 1663): DUN STATE [DUN_STATE_IDLE --> DUN_STATE_IDLE][3 Event]
E/QCvdec  ( 1389): Setparameter: unknown param 2130706451
E/tag     ( 2125): surfaceChanged width = 300,height=200
E/SystemPlayer( 2125): mFullScreenOnClickListener-->width=0;height=0
V/tag     ( 2125): system:changeBattery100:76
E/        ( 2125): 15
E/SystemPlayer( 2125): mFullScreenOnClickListener-->width=0;height=0
V/tag     ( 2125): system:changeBattery100:76
E/        ( 2125): 15
E/SystemPlayer( 2125): mFullScreenOnClickListener-->width=0;height=0
V/tag     ( 2125): system:changeBattery100:76
E/        ( 2125): 15
E/SystemPlayer( 2125): onVideoSizeChanged()-->width=480;height=320
V/AudioHardwareMSM72XX( 1389): open driver
V/AudioHardwareMSM72XX( 1389): get config
V/AudioHardwareMSM72XX( 1389): set config
V/AudioHardwareMSM72XX( 1389): buffer_size: 4800
V/AudioHardwareMSM72XX( 1389): buffer_count: 2
V/AudioHardwareMSM72XX( 1389): channel_count: 2
V/AudioHardwareMSM72XX( 1389): sample_rate: 44100
I/ActivityManager( 1457): Displayed com.clov4r.android.nil/.SystemPlayer: +3s248ms (total +3s538ms)
E/tag     ( 2125): surfaceChanged width = 480,height=320
E/QCvdec  ( 1389): Error: get_config Not Implemented
E/SystemPlayer( 2125): mFullScreenOnClickListener-->width=320;height=320
E/SystemPlayer( 2125): mFullScreenOnClickListener-->displayMode=1
V/tag     ( 2125): system:changeBattery100:76
E/        ( 2125): 15
V/item    ( 2125): write  success!
V/tag     ( 2125): system:changeBattery100:76
E/        ( 2125): 15
V/tag     ( 2125): system:changeBattery100:76
E/        ( 2125): 15
V/tag     ( 2125): system:changeBattery100:76
E/        ( 2125): 15
V/tag     ( 2125): system:changeBattery100:76
E/        ( 2125): 15
V/tag     ( 2125): system:changeBattery100:76
E/        ( 2125): 15


```

---

### Post by williammanda on 2011-12-20
I wanted post an updated logcat snapshot for the freezing video.

This is when the video is started then it plays for 10 seconds and the video freezes but the audio continues.

```
V/AudioHardwareMSM72XX( 1391): open driver
V/AudioHardwareMSM72XX( 1391): get config
V/AudioHardwareMSM72XX( 1391): set config
V/AudioHardwareMSM72XX( 1391): buffer_size: 4800
V/AudioHardwareMSM72XX( 1391): buffer_count: 2
V/AudioHardwareMSM72XX( 1391): channel_count: 2
V/AudioHardwareMSM72XX( 1391): sample_rate: 44100
W/ciq     ( 2769): browserCallEvent() EVENT_DATA_RCV_FINISH - Invalid sequence
I/ActivityManager( 1472): Starting: Intent { act=android.intent.action.VIEW dat=http://192.168.1.100/mythexport/video/WNABDT-Everybody_Loves_Raymond-Marie_s_Meatballs-2011120502.mp4 typ=video/mp4 cmp=com.clov4r.android.nil/.MainActivity } from pid 2769
V/mytag   ( 2825): onCreate
V/tag     ( 2825): currentPlayMode=false
V/item    ( 2825): read  success!
V/item    ( 2825): read file success!
V/item    ( 2825): read  success!
I/ActivityManager( 1472): Starting: Intent { cmp=com.clov4r.android.nil/.SystemPlayer (has extras) } from pid 2825
W/AudioFlinger( 1391): write blocked for 230 msecs, 17 delayed writes, thread 0xcc58
W/ActivityManager( 1472): Activity pause timeout for HistoryRecord{40602cc8 com.clov4r.android.nil/.MainActivity}
W/Resources( 2825): Converting to string: TypedValue{t=0x12/d=0x0 a=3 r=0x7f090023}
V/item    ( 2825): read file success!
W/drawable( 2825): Bad element under <shape>: background
W/Resources( 2825): Converting to string: TypedValue{t=0x12/d=0x0 a=3 r=0x7f090023}
W/ciq     ( 2769): browserCallEvent() EVENT_PAGE_RENDER_FINISH - Invalid sequence
E/QCvdec  ( 1391): Setparameter: unknown param 2130706451
E/tag     ( 2825): surfaceChanged width = 300,height=200
E/SystemPlayer( 2825): mFullScreenOnClickListener-->width=0;height=0
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
E/SystemPlayer( 2825): mFullScreenOnClickListener-->width=0;height=0
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
E/SystemPlayer( 2825): mFullScreenOnClickListener-->width=0;height=0
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
E/SystemPlayer( 2825): onVideoSizeChanged()-->width=480;height=320
W/IInputConnectionWrapper( 2769): showStatusIcon on inactive InputConnection
I/ActivityManager( 1472): Displayed com.clov4r.android.nil/.SystemPlayer: +3s951ms (total +4s527ms)
V/AudioHardwareMSM72XX( 1391): open driver
V/AudioHardwareMSM72XX( 1391): get config
V/AudioHardwareMSM72XX( 1391): set config
V/AudioHardwareMSM72XX( 1391): buffer_size: 4800
V/AudioHardwareMSM72XX( 1391): buffer_count: 2
V/AudioHardwareMSM72XX( 1391): channel_count: 2
V/AudioHardwareMSM72XX( 1391): sample_rate: 44100
E/tag     ( 2825): surfaceChanged width = 480,height=320
E/QCvdec  ( 1391): Error: get_config Not Implemented
E/SystemPlayer( 2825): mFullScreenOnClickListener-->width=320;height=320
E/SystemPlayer( 2825): mFullScreenOnClickListener-->displayMode=1
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/item    ( 2825): write  success!
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20


```

This is after the video freezes and I skip forward and the video continues to play for 10 seconds and then freezes.

```
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/hx      ( 2825): CurrentPosition=77728
V/hx      ( 2825): Duration=1797329
V/hx      ( 2825): seek to=107728
E/QCvdec  ( 1391): Omx Flush issued when vdec is not initialized yet.
E/        ( 1391): Flush VDL_stats_q: stats_ptr 0xdc5e0
E/QCvdec  ( 1391): Warning - previous ts > current ts. And both are non B-frames
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/hx      ( 2825): CurrentPosition=121088
V/hx      ( 2825): Duration=1797329
V/hx      ( 2825): seek to=151088
E/QCvdec  ( 1391): Omx Flush issued when vdec is not initialized yet.
E/        ( 1391): Flush VDL_stats_q: stats_ptr 0xdc610
E/QCvdec  ( 1391): Warning - previous ts > current ts. And both are non B-frames
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20
V/tag     ( 2825): system:changeBattery100:100
E/        ( 2825): 20


```

This is my log info:

Portable H264 Low Res - Changed audio freq to 44100 logcat info. Result - Video is great and audio is in sync but video still freezes after 10 sec. ELR Maries Meatballs.
Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=10-51, pass 2, 384 kb/s, 60k tbn, 59.94 tbc
Stream #0.1(eng): Audio: libfaac, 44100 Hz, 2 channels, s16, 64 kb/s

---

### Post by williammanda on 2011-12-23
Note:
I tried out VLC stream  and convert and the result was good. I set it up for H264 and every recording and video I tried worked. Also as an added feature, VLC streamed the recording / video with minor cpu load. I went this route in hopes that I could see something that would help correct my Mythexport problem. So for now I know that the phone will work.

---

