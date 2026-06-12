---
title: "gstreamer: convert mp3 to ogg"
date: 2011-01-31
forum: Multimedia Software
---

### Post by trldp on 2011-01-31
When I try to convert an mp3 to an ogg file with gstreamer like this:
```
gst-launch-0.10 -v filesrc location=infile.mp3 ! decodebin2 location=infile.mp3 ! audioconvert ! vorbisenc ! oggmux ! filesink location=outfile.ogg
```everything works file, but when I add a bitrate option to vorbisenc, like this
```
gst-launch-0.10 -v filesrc location=infile.mp3 ! decodebin2  location=infile.mp3 ! audioconvert ! vorbisenc bitrate=12800 ! oggmux ! filesink  location=outfile.ogg
```gstreamer crashes with the following output:
```
Pijplijn gezet op gepauzeerd ...
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind.GstPad:src: caps = application/x-id3
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/GstID3Demux:id3demux0.GstPad:sink: caps = application/x-id3
Pijplijn is bezig met PREROLL ...
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/GstMPEGAudioParse:mpegaudioparse0.GstPad:sink: caps = audio/mpeg, mpegversion=(int)1, layer=(int)3
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/GstMPEGAudioParse:mpegaudioparse0.GstPad:src: caps = audio/mpeg, mpegversion=(int)1, mpegaudioversion=(int)2, layer=(int)3, rate=(int)22050, channels=(int)1, parsed=(boolean)true
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/FluMp3Dec:flump3dec0.GstPad:sink: caps = audio/mpeg, mpegversion=(int)1, mpegaudioversion=(int)2, layer=(int)3, rate=(int)22050, channels=(int)1, parsed=(boolean)true
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20.GstDecodePad:src0: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)22050, channels=(int)1
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/FluMp3Dec:flump3dec0.GstPad:src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)22050, channels=(int)1
/GstPipeline:pipeline0/GstAudioConvert:audioconvert0.GstPad:src: caps = audio/x-raw-float, rate=(int)22050, channels=(int)1, endianness=(int)1234, width=(int)32
/GstPipeline:pipeline0/GstAudioConvert:audioconvert0.GstPad:sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)22050, channels=(int)1
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20.GstDecodePad:src0.GstProxyPad:proxypad5: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)22050, channels=(int)1
/GstPipeline:pipeline0/GstVorbisEnc:vorbisenc0: last-message = "encoding at approximate bitrate 128000 bps (VBR encoding enabled)"
FOUT: van element /GstPipeline:pipeline0/GstFileSrc:filesrc0: Interne fout met gegevensdoorvoer.
Extra debug-informatie:
gstbasesrc.c(2550): gst_base_src_loop (): /GstPipeline:pipeline0/GstFileSrc:filesrc0:
streaming task paused, reason not-negotiated (-4)
FOUT: pijplijn wil niet PREROLL uitvoeren.
Pijplijn gezet op NULL ...
/GstPipeline:pipeline0/GstAudioConvert:audioconvert0.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstAudioConvert:audioconvert0.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20.GstDecodePad:src0: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/FluMp3Dec:flump3dec0.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/FluMp3Dec:flump3dec0.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/GstMPEGAudioParse:mpegaudioparse0.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/GstMPEGAudioParse:mpegaudioparse0.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/GstID3Demux:id3demux0.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/GstID3Demux:id3demux0.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind.GstPad:src: caps = NULL
Pijplijn wordt vrijgemaakt ...
```btw. when I try to convert flac files this way, everything works fine

---

### Post by kn0w-b1nary on 2011-01-31
why not use VLC media player?

---

### Post by trldp on 2011-02-01
In fact I'm writing a program using gstreamer, and also in this program it doesn't work.

---

### Post by kn0w-b1nary on 2011-02-01
> **trldp said:**
> In fact I'm writing a program using gstreamer, and also in this program it doesn't work.

Could you give some more detail? I'm not sure i understand what you're saying.

---

### Post by sydbat on 2011-02-01
Why not use Sound Converter. It's in Synaptic. You can set bitrate to whatever you want.

---

### Post by trldp on 2011-02-04
Well I'm writing a program that does some things for me (like converting music, synchronizing with the music of my brothers and so on). In this program I use gstreamer. I've written the following code (it's vala code):

```

class Encoder
{
  public bool convert ()
  {
       
    pipeline = new Gst.Pipeline ("total-pipeline");
    
    //Element that reads the file
    Gst.Element filesrc = Gst.ElementFactory.make ("filesrc", "file-source");
    filesrc.set ("location", input_file.filename);
    pipeline.add (filesrc);
    
    //Element that decodes the file
    Gst.Element decoder = Gst.ElementFactory.make ("decodebin2", "decoder");
    pipeline.add (decoder);
    filesrc.link (decoder);
    
    //Element that converts the output of decodebin to something that vorbisenc and
    //flacenc can read
    Gst.Element audioconvert = Gst.ElementFactory.make ("audioconvert", "audioconvert");
    pipeline.add (audioconvert);
    
    Gst.Bin encoder_bin;
    
    switch (output_format)
    {
      case Format.OGG:
        if (output_bitrate != -1)
          encoder_bin = new OggEncoder (output_bitrate);
        else
          encoder_bin = new OggEncoder ();
      break;
      case Format.FLAC:
        encoder_bin = new FlacEncoder ();
      break;
      default:
        Main.notify ("Unexpected output_format: %s".printf (output_format.to_string()),
                     MessageType.WARNING);
        return false;
    }
    pipeline.add (encoder_bin);
    audioconvert.link (encoder_bin);
    
    //Element that writes the file
    Gst.Element filesink = Gst.ElementFactory.make ("filesink", "sink");
    filesink.set ("location", output_file);
    pipeline.add (filesink);
    encoder_bin.link (filesink);
    
    //If there come a new path from decoder connect it to enc_bin
    Signal.connect (decoder, "new-decoded-pad",
                    (Callback) new_pad_from_decoder, audioconvert);
    
    //Set up a bus for watching the messages that come in the pipeline
    Gst.Bus bus = pipeline.get_bus ();
    bus.add_watch (bus_message);
    
    //Start encoding
    pipeline.set_state (Gst.State.PLAYING);
    loop.run ();
    
    return true;
  }

//Connect decoder with a sink
  private void new_pad_from_decoder (Gst.Pad pad, bool arg1, Gst.Element sink)
  {
    Gst.Pad sink_pad;
    
    sink_pad = sink.get_pad ("sink");
    pad.link (sink_pad);
  }
}

//Class that converts raw audio to the ogg vorbis format
public class OggEncoder : Gst.Bin
{
  /*
   *  Attributes
   */
  private Gst.Element encoder;
  private Gst.Element muxer;
  private int _bitrate = -1;
  
  /*
   *  Properties
   */ 
  [Description (nick = "Output bitrate",
   blurb = "The bitrate of the output file (in kbps)")]
  public int bitrate 
  { 
    get {return _bitrate;} 
    set 
    {
      _bitrate = value;
      
      encoder.set ("bitrate", _bitrate*1000);
    } 
  }
  
  /*
   *  Constructors
   */
  private OggEncoder.without_properties ()
  {
    encoder = Gst.ElementFactory.make ("vorbisenc", "encoder");
    this.add (encoder);
    
    muxer = Gst.ElementFactory.make ("oggmux", "muxer");
    this.add (muxer);
    encoder.link (muxer);
    
    //Create ghost pads for connecting elements outside the bin with the bin
    Gst.Pad encoder_pad = encoder.get_pad ("sink");
    Gst.Pad ghost_sink = new Gst.GhostPad ("sink", encoder_pad);
    this.add_pad (ghost_sink);
    
    Gst.Pad muxer_pad = muxer.get_pad ("src");
    Gst.Pad ghost_source = new Gst.GhostPad ("src", muxer_pad);
    this.add_pad (ghost_source);
  }
   
  public OggEncoder (int bitrate = 128)
  {    
    this.without_properties ();
    
    this.bitrate = bitrate;
  }
}

class FlacEncoder
{
  //Not important, it works perfect
}

```This program does more or less the same as (At the moment both crashes)
```

gst-launch-0.10 -v filesrc location=infile.mp3 ! decodebin2 location=infile.mp3 ! audioconvert ! vorbisenc ! oggmux ! filesink location=outfile.ogg

```So I suppose that either there is a bug in gstreamer, or I'm connecting the wrong pipelines.

---

### Post by NFblaze on 2011-02-04
Not sure about this, but I think the gstreamer OGG pipe uses quality and not bitrate, as in one of the paramaters should be quality=.6 or something. I'll google it and be back

So I googled it and happened upon [gstreamer documentation for vorbisenc]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-base-plugins/html/gst-plugins-base-plugins-vorbisenc.html#GstVorbisEnc--bitrate")

looks like it's accepted but even the documentation reccommend the quality parameter. Though, I am clueless as to why it wont accept your bitrate

---

### Post by trldp on 2011-02-05
Well, indeed with the quality option it seems to work. Thanks

---

