---
title: "Audio passthrough on Pandaboard using ALSA API"
date: 2014-02-28
forum: Multimedia Software
---

### Post by VadimIzmalkov on 2014-02-28
[COLOR=#333333][FONT=Arial]Hello All.

I created simple application that makes audio pass-through (from analog input to analog output), 

After 2-10 seconds get error like:
**AlsaPassthrough: pcm.c:693: snd_pcm_close: Assertion `pcm' failed.**
or 
**write to audio interface failed (Broken pipe)**

Seems I have problem with buffer size/time or somethink like that.
Parameters used:
Buffer - 100 ms / 4800 frames / 19200 bytes
Period - 10 ms / 480 frames / 1920 bytes

Buffer length used 19200 bytes. [/FONT][/COLOR][FONT=Arial]
[TABLE="width: 653"]
[TR]
[TD="class: gutter"][RIGHT]1[/RIGHT]
[/TD]
[TD="class: code"]char buffer[19200];
[/TD]
[/TR]
[/TABLE]


Write/read function used as follow
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][COLOR=white !important][FONT=Consolas][?]("http://e2e.ti.com/support/omap/f/849/t/324582.aspx#")[/FONT][/FONT][/COLOR][FONT=Arial]
[TABLE="width: 668"]
[TR]
[TD="class: gutter"][RIGHT]1
2[/RIGHT]
[/TD]
[TD="class: code"]snd_pcm_readi(pcm, buffer, frames);
snd_pcm_writei(pcm, buffer, frames);
[/TD]
[/TR]
[/TABLE]


Have somebody any suggestion?
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Segments of the code you can find bellow.

Alsamixer settings:[/FONT][/COLOR][FONT=Arial]
[TABLE="width: 668"]
[TR]
[TD="class: gutter"][RIGHT]1
2
3
4
5
6
7
8[/RIGHT]
[/TD]
[TD="class: code"]amixer cset name='Analog Left Capture Route' 'Headset Mic'
amixer cset name='Analog Right Capture Route' 'Headset Mic'
amixer cset name='MUX_UL00' 'AMic0'
amixer cset name='MUX_UL01' 'AMic1'
amixer cset name='Headset Left Playback' 'HS DAC'
amixer cset name='Headset Right Playback' 'HS DAC'
amixer cset name='Headset Playback Volume' 100
amixer cset name='DL1 Media' 120
[/TD]
[/TR]
[/TABLE]


Structure for the devices:[/FONT][FONT=Arial]
[TABLE="width: 668"]
[TR]
[TD="class: gutter"][RIGHT]1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20[/RIGHT]
[/TD]
[TD="class: code"]typedef struct
{
    char *deviceName;

    snd_pcm_t *pcm;
    snd_pcm_hw_params_t *hwParams;
    snd_pcm_stream_t stream;
    snd_pcm_access_t access;
    snd_pcm_format_t format;
    snd_pcm_uframes_t frames;

    int mode;

    unsigned int sampleRate;

    unsigned int bufferTime;
    unsigned int periodTime;
    unsigned int channels;

} pcmDevice_t;
[/TD]
[/TR]
[/TABLE]


Parameters for capture:[/FONT][FONT=Arial]
[TABLE="width: 668"]
[TR]
[TD="class: gutter"][RIGHT]1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20[/RIGHT]
[/TD]
[TD="class: code"]pcmDevice_t* initRecordDevice()
{
    pcmDevice_t *device;

    device = malloc(sizeof(pcmDevice_t));

    device->deviceName = strdup("plughw:0,0");

    device->stream = SND_PCM_STREAM_CAPTURE;
    device->access = SND_PCM_ACCESS_RW_INTERLEAVED;
    device->format = SND_PCM_FORMAT_S16_LE;
    device->mode = 0; //SND_PCM_ASYNC; //SND_PCM_NONBLOCK;

    device->sampleRate = 48000;
    device->bufferTime = 100 * 1000; // 100 ms
    device->periodTime = 10 * 1000; // 20ms
    device->channels = 2;

    return device;
}
[/TD]
[/TR]
[/TABLE]


Parameters for playback:[/FONT][FONT=Arial]
[TABLE="width: 668"]
[TR]
[TD="class: gutter"][RIGHT]1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20[/RIGHT]
[/TD]
[TD="class: code"]pcmDevice_t* initPlaybackDevice()
{
    pcmDevice_t *device;

    device = malloc(sizeof(pcmDevice_t));

    device->deviceName = strdup("plughw:0,0");

    device->stream = SND_PCM_STREAM_PLAYBACK;
    device->access = SND_PCM_ACCESS_RW_INTERLEAVED;
    device->format = SND_PCM_FORMAT_S16_LE;
    device->mode = 0; //SND_PCM_ASYNC; //SND_PCM_NONBLOCK;

    device->sampleRate = 48000;
    device->bufferTime = 100 * 1000; // 100 ms
    device->periodTime = 10 * 1000; // 20ms
    device->channels = 2;

    return device;
}
[/TD]
[/TR]
[/TABLE]


Setup devices:[/FONT][FONT=Arial]
[TABLE="width: 774"]
[TR]
[TD="class: gutter"][RIGHT]1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75[/RIGHT]
[/TD]
[TD="class: code"]int setupDevice(pcmDevice_t *device)
{
    int err;
    /* Open PCM. The last parameter of this function is the mode. */
    /* If this is set to 0, the standard mode is used. Possible   */
    /* other values are SND_PCM_NONBLOCK and SND_PCM_ASYNC.       */
    /* If SND_PCM_NONBLOCK is used, read / write access to the    */
    /* PCM device will return immediately. If SND_PCM_ASYNC is    */
    /* specified, SIGIO will be emitted whenever a period has     */
    /* been completely processed by the soundcard.                */
    if ((err = snd_pcm_open(&device->pcm, device->deviceName, device->stream, device->mode)) < 0) {
        fprintf (stderr, "cannot open audio device %s (%s)\n", device->deviceName, snd_strerror (err));
        exit (1);
    }

    if ((err = snd_pcm_hw_params_malloc (&device->hwParams)) < 0) {
        fprintf (stderr, "cannot allocate hardware parameter structure (%s)\n", snd_strerror (err));
        exit (1);
    }

    if ((err = snd_pcm_hw_params_any (device->pcm, device->hwParams)) < 0) {
        fprintf (stderr, "cannot initialize hardware parameter structure (%s)\n", snd_strerror (err));
        exit (1);
    }

    if ((err = snd_pcm_hw_params_set_access (device->pcm, device->hwParams, device->access)) < 0) {
        fprintf (stderr, "cannot set access type (%s)\n", snd_strerror (err));
        exit (1);
    }

    if ((err = snd_pcm_hw_params_set_format (device->pcm, device->hwParams, device->format)) < 0) {
        fprintf (stderr, "cannot set sample format (%s)\n", snd_strerror (err));
        exit (1);
    }

    if ((err = snd_pcm_hw_params_set_buffer_time_near (device->pcm, device->hwParams, &device->bufferTime, NULL)) < 0) {
        fprintf (stderr, "cannot set buffer size (%s)\n", snd_strerror (err));
        exit (1);
    } else {
        /* Set buffer size (in frames). The resulting latency is given by */
        /* latency = periodsize * periods / (rate * bytes_per_frame)      */
        snd_pcm_hw_params_get_buffer_size(device->hwParams, &device->frames);
    }

    if ((err = snd_pcm_hw_params_set_period_time_near (device->pcm, device->hwParams, &device->periodTime, NULL)) < 0) {
        fprintf (stderr, "cannot set period size (%s)\n", snd_strerror (err));
        exit (1);
    }

    if ((err = snd_pcm_hw_params_set_rate_near (device->pcm, device->hwParams, &device->sampleRate, NULL)) < 0) {
        fprintf (stderr, "cannot set sample rate (%s)\n", snd_strerror (err));
        exit (1);
    }

    if ((err = snd_pcm_hw_params_set_channels (device->pcm, device->hwParams, device->channels)) < 0) {
        fprintf (stderr, "cannot set channel count (%s)\n",     snd_strerror (err));
        exit (1);
    }

    /* Apply HW parameter settings to */
    /* PCM device and prepare device  */
    if ((err = snd_pcm_hw_params (device->pcm, device->hwParams)) < 0) {
        fprintf (stderr, "cannot set parameters (%s)\n", snd_strerror (err));
        exit (1);
    }

    snd_pcm_hw_params_free (device->hwParams);

    if ((err = snd_pcm_prepare (device->pcm)) < 0) {
        fprintf (stderr, "cannot prepare audio interface for use (%s)\n", snd_strerror (err));
        exit (1);
    }

    return 0;
}
[/TD]
[/TR]
[/TABLE]


Main:[/FONT][FONT=Arial]
[TABLE="width: 668"]
[TR]
[TD="class: gutter"][RIGHT]1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48[/RIGHT]
[/TD]
[TD="class: code"]main (int argc, char *argv[])
{
    int i;
    int err;

    char buf[4800*4];

    snd_pcm_t *capture_handle;
    snd_pcm_hw_params_t *hw_params;
    snd_pcm_uframes_t frames;

    pcmDevice_t *pcmRecord;
    pcmDevice_t *pcmPlayback;

    pcmRecord    = initRecordDevice();
    pcmPlayback = initPlaybackDevice();

    printf("\n----------- RECORD DEVICE -----------\n");
    setupDevice(pcmRecord);
    showConfig(pcmRecord);

    printf("\n---------- PLAYBACK DEVICE ----------\n");
    setupDevice(pcmPlayback);
    showConfig(pcmPlayback);

    for (i = 0; i < 100; ++i) {
        /* Read num_frames frames from the PCM device  */
        /* pointed to by pcm_handle to buffer capdata. */
        /* Returns the number of frames actually read. */
        //if((err = snd_pcm_readi (pcmRecord->pcm, buf, pcmRecord->frames)) != pcmRecord->frames) {
        if((err = snd_pcm_readi (pcmRecord->pcm, buf, 480)) != 480) {
            fprintf (stderr, "read from audio interface failed (%s)\n", snd_strerror (err));
            exit (1);
        }

        /* Write num_frames frames from buffer data to    */
        /* the PCM device pointed to by pcm_handle.       */
        /* Returns the number of frames actually written. */
        if((err = snd_pcm_writei (pcmPlayback->pcm, buf, pcmRecord->frames)) != pcmRecord->frames) {
            fprintf (stderr, "write to audio interface failed (%s)\n", snd_strerror (err));
            exit (1);
        }
    }

    snd_pcm_close (capture_handle);
    exit (0);

}[/TD]
[/TR]
[/TABLE]
[/FONT]

---

