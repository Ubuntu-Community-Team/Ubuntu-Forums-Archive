---
title: "v4l2 Easycab video recording image quality too black too red too dark"
date: 2018-02-05
forum: Multimedia Software
---

### Post by xinuzi on 2018-02-05
Hi,

*[Error: EasycaB in the title must be EasyCAP, sorry]*

Have been having trouble recording with this **EasyCAP** stick 
(*ID 1b71:3002 Fushicai USBTV007 Video Grabber [EasyCAP]*) on Linux Lubuntu X64.
TV/recorder (PAL) to scart to composite to usb.

*Driver Info (not using libv4l2):*
*    Driver name   : usbtv*
*    Card type     : usbtv*
*    Bus info      : usb-0000:00:12.2-1*
*    Driver version: 4.13.13*
*    Capabilities  : 0x85200001*
*        Video Capture*
*        Read/Write*
*        Streaming*
*        Extended Pix Format*
*        Device Capabilities*
*    Device Caps   : 0x05200001*
*        Video Capture*
*        Read/Write*
*        Streaming*
*        Extended Pix Format*

The input can be too dark, too red, too shadowed.
You could start to think this is due to the EasyCAP-stick, but this cheap recording USB-stick actually works very well once you figure out the right settings.

Apparently the only thing that needs to get set is the brightness, and possibly the saturation, in order to become a 
much better picture quality of the video.

v4l2-ctl -d /dev/video0 -l result:

*User Controls*

*                     brightness (int)    : min=0 max=1023 step=1 default=448 value=448 flags=slider*
*                       contrast (int)    : min=0 max=1023 step=1 default=464 value=464 flags=slider*
*                     saturation (int)    : min=0 max=1023 step=1 default=512 value=512 flags=slider*
*                            hue (int)    : min=-3583 max=3583 step=1 default=0 value=0 flags=slider*
*                      sharpness (int)    : min=0 max=255 step=1 default=96 value=96 flags=sliders*
                      
Dilemma: settings not settable with 'v4l2-ctl -d /dev/video0 --set-ctrl=brightness=596' e.g. ('Invalid argument').

The same v4l2-controls are present and changeable in VLC, but when I record to file the settings aren't preserved and 
the resulting vid is again too dark, too red, too shadowed.

The one thing that does the thing for me is this:

Use **OBS** together with **qv4l2 (Qt v4l2 test Utility)** (after having installed v4l2-utils of course) . More specifically the 'User Controls' in qv4l2.
Open OBS and leave Qt v4l2 test Utility open simultaneously.

Slightly moving the brightness slider in qv4l2 suddenly gives a close to perfect image quality at a certain point.
 
The effect can be seen immediately in OBS and the recording can be saved to a video file (in this case mpeg4-mp3-mkv-1400kbps) 
with the made v4l2 changes.

OBS also contains filter settings for chroma and color, but it is not the same as tuning the v4l2 brightness. The OBS filters can
easily distort the video image even more.

If you change settings in OBS while qv4l2 is open it could happen that you have to reset the brightness and saturation anew in qv4l2 afterwards.


Before...
[ATTACH=CONFIG]278442[/ATTACH]

After...
[ATTACH=CONFIG]278443[/ATTACH]

Finally, **OBS settings that work for me**:

**Sources:**

- Add Video-capture (v4L2), rightclick, select device USBTV in Properties; select Filters and add video filter 'Scaling', click it and set to Bilinear 16:9.
- Audio input(PulseAudio): depends on the system. The one where I can select Device USBTV007 Video Grabber [EasyCAP] Analogue stereo. Even if you don't hear audio in OBS, it will be present in the resulting video file.

**General settings:**

- Advanced/Video: Color=NV12; YUV=601 Partial.
- Video: Basic & Output resolution: 1280x720; Filter: Bilinear 30fps (the other filters can slow down the recording of the video image).
- Audio: everything on 128 kbps.
- Output/Record: FFmpeg to file; filename without spaces; matroska (mkv); video Bitrate: 1400 kbps (personal choice, influences size of file); time between keyframes: 50; scaling: 640x360 (or 1280x720); show all codecs; mpeg4 (standard) (more flexible than x264 in after-cutting); Video encodersettings: -r 25 (because the EasyCAP records at 25fps -> better sync video - audio if you set this); Audio bitrate: 128 libmp3lame.

---

