---
title: "Howto fix transcoding to PSP format in newer versions of Avidemux"
date: 2010-09-12
forum: Multimedia Software
---

### Post by Jungleboss on 2010-09-12
**[UPDATED] Thanks bastafidli!**

In newer versions of Avidemux wrong parameters are set when choosing "Sony Playstation Portable" from the Auto menu. The PSP doesn't support more than 2 reference frames or 8x8 DCT Transform.

This is how you can fix it.

Backup the original file
```
sudo cp /usr/lib/ADM_plugins/videoEncoder/x264/Sony\ PlayStation\ Portable.xml /usr/lib/ADM_plugins/videoEncoder/x264/Sony\ PlayStation\ Portable.xml.org

```
Edit the file
```
sudo gedit /usr/lib/ADM_plugins/videoEncoder/x264/Sony\ PlayStation\ Portable.xml
```

Change this line
```
<referenceFrames>3</referenceFrames>
```
to
```
<referenceFrames>2</referenceFrames>
```
Add this line to the **x264Options** section
```
<bFrameReferences>none</bFrameReferences>
```
and add this line to the **analyse** section.
```
<dct8x8>false</dct8x8>
```

This is how the new file should look

```
<?xml version='1.0'?>
<x264Config>
  <encodeOptions>
    <mode>2PASS ABR</mode>
    <parameter>1000</parameter>
  </encodeOptions>
  <x264Options>
    <idcLevel>30</idcLevel>
    **<referenceFrames>2</referenceFrames>**
    <bFrames>3</bFrames>
    <adaptiveBframeDecision>2</adaptiveBframeDecision>
    **<bFrameReferences>none</bFrameReferences>**
    <analyse>
      <partitionI4x4>true</partitionI4x4>
      <partitionI8x8>false</partitionI8x8>
      <partitionP8x8>true</partitionP8x8>
      <partitionP4x4>false</partitionP4x4>
      <partitionB8x8>true</partitionB8x8>
      **<dct8x8>false</dct8x8>**
      <weightedPrediction>true</weightedPrediction>
      <directPredictionMode>auto</directPredictionMode>
      <motionEstimationMethod>multi-hexagonal</motionEstimationMethod>
      <subpixelRefinement>7</subpixelRefinement>
      <mixedReferences>true</mixedReferences>
      <trellis>finalMacroblock</trellis>
    </analyse>
    <rateControl>
      <vbvMaximumBitrate>10000</vbvMaximumBitrate>
      <vbvBufferSize>10000</vbvBufferSize>
    </rateControl>
  </x264Options>
</x264Config>

```

This is now identical to bastafidli's fix below.

---

### Post by bastafidli on 2010-09-24
The above fix is not complete, it also requires

<bFrameReferences>none</bFrameReferences>

When using Avidemux 2.5.3 you need to install the following patch

[http://avidemux.org/admForum/viewtopic.php?id=7926](http://avidemux.org/admForum/viewtopic.php?id=7926)

That will provide the correct profile with all the fixes mentioned above + more.

---

