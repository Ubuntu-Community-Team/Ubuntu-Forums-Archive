---
title: "Setup nvidia-settings through CLI?"
date: 2011-08-02
forum: Multimedia Software
---

### Post by eyerouge on 2011-08-02
**info**
All works when I use the GUI for nvidia-settings and I have *no issues.* I will happily buy whoever helps me with this little trick a coffee though, given (s)he can handle paypal;)

**what i want**
When using dual screens I want to:

[LIST=1]
[*]Shut the laptops screen off
[*]Turn the other external screen on...
[*]with twin view enabled...
[*]and also set the resolution on the external screen to 1920x1080 (it defaults to 1400 x something since its my laptops screens native res, so I have to change it all the time). 
[/LIST]

I want to do that *without* using the darn nvidia-settings GUI, since it involves plenty of clicking and gets tedious when you do it at least 5 times a day (I move around a lot on my work etc). 

I also don't want the settings saved in the nvidia config file since I connect the computer to different monitors often, and finally I want the commands to do the reverse: Shut the external one off, and set the laptops screen on. 

**how?**
I know I'm supposed to use the --assign switch but I can't figure it out and get plenty of messages like for example:
```

ERROR: The attribute 'FrontendResolution' specified in assignment
       '[GPU:0]/FrontendResolution[DFP-1]=1600,900' cannot be assigned (it is a read-only attribute).
```

Could anyone show me the light here?

**software**
Ubuntu 11.04 (64)

**hardware**
Laptop, MacBook Air 3,2, normal resolution on it's screen is 1440x900


**screenshots**
1.[IMG]http://chaosrealm.net/wtactics/files/pics/xservinfo.png[/IMG]

2.[IMG]http://chaosrealm.net/wtactics/files/pics/2011_08_03_03.png[/IMG]

3.[IMG]http://chaosrealm.net/wtactics/files/pics/2011_08_03_04.png[/IMG]

**more info**
*nvidia-settings --query all* gives me: 




```

Attributes queryable via air:0.0:

  Attribute 'OperatingSystem' (air:0.0): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2 (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (air:0.0): 270.41.06 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen, GPU.

  Attribute 'NvControlVersion' (air:0.0): 1.26 
    'NvControlVersion' is a string attribute.
    'NvControlVersion' is a read-only attribute.
    'NvControlVersion' can use the following target types: X Screen.

  Attribute 'GLXServerVersion' (air:0.0): 1.4 
    'GLXServerVersion' is a string attribute.
    'GLXServerVersion' is a read-only attribute.
    'GLXServerVersion' can use the following target types: X Screen.

  Attribute 'GLXClientVersion' (air:0.0): 1.4 
    'GLXClientVersion' is a string attribute.
    'GLXClientVersion' is a read-only attribute.
    'GLXClientVersion' can use the following target types: X Screen.

  Attribute 'OpenGLVersion' (air:0.0): 3.3.0 NVIDIA 270.41.06 
    'OpenGLVersion' is a string attribute.
    'OpenGLVersion' is a read-only attribute.
    'OpenGLVersion' can use the following target types: X Screen.

  Attribute 'XRandRVersion' (air:0.0): 1.3 
    'XRandRVersion' is a string attribute.
    'XRandRVersion' is a read-only attribute.
    'XRandRVersion' can use the following target types: X Screen.

  Attribute 'XF86VidModeVersion' (air:0.0): 2.2 
    'XF86VidModeVersion' is a string attribute.
    'XF86VidModeVersion' is a read-only attribute.
    'XF86VidModeVersion' can use the following target types: X Screen.

  Attribute 'XvVersion' (air:0.0): 2.2 
    'XvVersion' is a string attribute.
    'XvVersion' is a read-only attribute.
    'XvVersion' can use the following target types: X Screen.

  Attribute 'TwinView' (air:0.0): 1.
    'TwinView' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'TwinView' is a read-only attribute.
    'TwinView' can use the following target types: X Screen.

  Attribute 'ConnectedDisplays' (air:0.0): 0x00060000.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (air:0.0): 0x00060000.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'CursorShadow' (air:0.0): 0.
    'CursorShadow' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'CursorShadow' can use the following target types: X Screen.

  Attribute 'CursorShadowAlpha' (air:0.0): 64.
    The valid values for 'CursorShadowAlpha' are in the range 0 - 254 (inclusive).
    'CursorShadowAlpha' can use the following target types: X Screen.

  Attribute 'CursorShadowRed' (air:0.0): 0.
    The valid values for 'CursorShadowRed' are in the range 0 - 255 (inclusive).
    'CursorShadowRed' can use the following target types: X Screen.

  Attribute 'CursorShadowGreen' (air:0.0): 0.
    The valid values for 'CursorShadowGreen' are in the range 0 - 255 (inclusive).
    'CursorShadowGreen' can use the following target types: X Screen.

  Attribute 'CursorShadowBlue' (air:0.0): 0.
    The valid values for 'CursorShadowBlue' are in the range 0 - 255 (inclusive).
    'CursorShadowBlue' can use the following target types: X Screen.

  Attribute 'CursorShadowXOffset' (air:0.0): 4.
    The valid values for 'CursorShadowXOffset' are in the range 0 - 32 (inclusive).
    'CursorShadowXOffset' can use the following target types: X Screen.

  Attribute 'CursorShadowYOffset' (air:0.0): 2.
    The valid values for 'CursorShadowYOffset' are in the range 0 - 32 (inclusive).
    'CursorShadowYOffset' can use the following target types: X Screen.

  Attribute 'AssociatedDisplays' (air:0.0): 0x00060000.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.

  Attribute 'InitialPixmapPlacement' (air:0.0): 2.
    The valid values for 'InitialPixmapPlacement' are in the range 0 - 4 (inclusive).
    'InitialPixmapPlacement' can use the following target types: X Screen.

  Attribute 'DynamicTwinview' (air:0.0): 1.
    'DynamicTwinview' is an integer attribute.
    'DynamicTwinview' is a read-only attribute.
    'DynamicTwinview' can use the following target types: X Screen.

  Attribute 'MultiGpuDisplayOwner' (air:0.0): 0.
    'MultiGpuDisplayOwner' is an integer attribute.
    'MultiGpuDisplayOwner' is a read-only attribute.
    'MultiGpuDisplayOwner' can use the following target types: X Screen.

  Attribute 'GlyphCache' (air:0.0): 1.
    'GlyphCache' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GlyphCache' can use the following target types: X Screen.

  Attribute 'NotebookDisplayChangeLidEvent' (air:0.0): 1.
    'NotebookDisplayChangeLidEvent' is an integer attribute.
    'NotebookDisplayChangeLidEvent' can use the following target types: X Screen.

  Attribute 'NotebookInternalLCD' (air:0.0): 0x00040000.
    'NotebookInternalLCD' is a bitmask attribute.
    'NotebookInternalLCD' is a read-only attribute.
    'NotebookInternalLCD' can use the following target types: X Screen, GPU.

  Attribute 'Depth30Allowed' (air:0.0): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

  Attribute 'NoScanout' (air:0.0): 0.
    'NoScanout' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'NoScanout' is a read-only attribute.
    'NoScanout' can use the following target types: X Screen, GPU.

  Attribute 'XServerUniqueId' (air:0.0): 1757892753.
    'XServerUniqueId' is an integer attribute.
    'XServerUniqueId' is a read-only attribute.
    'XServerUniqueId' can use the following target types: X Screen.

  Attribute 'PixmapCache' (air:0.0): 1.
    'PixmapCache' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'PixmapCache' can use the following target types: X Screen.

  Attribute 'PixmapCacheRoundSizeKB' (air:0.0): 1024.
    The valid values for 'PixmapCacheRoundSizeKB' are in the range 4 - 1048576 (inclusive).
    'PixmapCacheRoundSizeKB' can use the following target types: X Screen.

  Attribute 'AccelerateTrapezoids' (air:0.0): 1.
    'AccelerateTrapezoids' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'AccelerateTrapezoids' can use the following target types: X Screen.

  Attribute 'SyncToVBlank' (air:0.0): 0.
    'SyncToVBlank' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'SyncToVBlank' can use the following target types: X Screen.

  Attribute 'LogAniso' (air:0.0): 0.
    The valid values for 'LogAniso' are in the range 0 - 4 (inclusive).
    'LogAniso' can use the following target types: X Screen.

  Attribute 'FSAA' (air:0.0): 0.
    Valid values for 'FSAA' are: 0, 1, 5, 7, 8, 9, 10 and 12.
    'FSAA' can use the following target types: X Screen.

  Attribute 'TextureSharpen' (air:0.0): 0.
    'TextureSharpen' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'TextureSharpen' can use the following target types: X Screen.

  Attribute 'AllowFlipping' (air:0.0): 1.
    'AllowFlipping' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'AllowFlipping' can use the following target types: X Screen.

  Attribute 'FSAAAppControlled' (air:0.0): 1.
    'FSAAAppControlled' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'FSAAAppControlled' can use the following target types: X Screen.

  Attribute 'LogAnisoAppControlled' (air:0.0): 1.
    'LogAnisoAppControlled' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'LogAnisoAppControlled' can use the following target types: X Screen.

  Attribute 'OpenGLImageSettings' (air:0.0): 1.
    The valid values for 'OpenGLImageSettings' are in the range 0 - 3 (inclusive).
    'OpenGLImageSettings' can use the following target types: X Screen.

  Attribute 'FSAAAppEnhanced' (air:0.0): 0.
    'FSAAAppEnhanced' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'FSAAAppEnhanced' can use the following target types: X Screen.

  Attribute 'SliMosaicModeAvailable' (air:0.0): 0.
    'SliMosaicModeAvailable' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'SliMosaicModeAvailable' is a read-only attribute.
    'SliMosaicModeAvailable' can use the following target types: X Screen, GPU, VCS.

  Attribute 'BusType' (air:0.0): 3.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU, SDI Input Device.

  Attribute 'VideoRam' (air:0.0): 262144.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.

  Attribute 'Irq' (air:0.0): 16.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU, SDI Input Device.

  Attribute 'CUDACores' (air:0.0): 48.
    'CUDACores' is an integer attribute.
    'CUDACores' is a read-only attribute.
    'CUDACores' can use the following target types: X Screen, GPU.

  Attribute 'GPUMemoryInterface' (air:0.0): 128.
    'GPUMemoryInterface' is an integer attribute.
    'GPUMemoryInterface' is a read-only attribute.
    'GPUMemoryInterface' can use the following target types: X Screen, GPU.

  Attribute 'GPUCoreTemp' (air:0.0): 67.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

  Attribute 'GPU2DClockFreqs' (air:0.0): 405,1064.
    The valid values for 'GPU2DClockFreqs' are in the ranges 101 - 810, 266 - 1276 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPU3DClockFreqs' (air:0.0): 450,1064.
    The valid values for 'GPU3DClockFreqs' are in the ranges 112 - 900, 266 - 1276 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault2DClockFreqs' (air:0.0): 405,1064.
    'GPUDefault2DClockFreqs' is a packed integer attribute.
    'GPUDefault2DClockFreqs' is a read-only attribute.
    'GPUDefault2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault3DClockFreqs' (air:0.0): 450,1064.
    'GPUDefault3DClockFreqs' is a packed integer attribute.
    'GPUDefault3DClockFreqs' is a read-only attribute.
    'GPUDefault3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentClockFreqs' (air:0.0): 450,1064.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentProcessorClockFreqs' (air:0.0): 950.
    The valid values for 'GPUCurrentProcessorClockFreqs' are in the range 237 - 1900 (inclusive).
    'GPUCurrentProcessorClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentClockFreqsString' (air:0.0): nvclock=450, memclock=1064, processorclock=950 
    'GPUCurrentClockFreqsString' is a string attribute.
    'GPUCurrentClockFreqsString' can use the following target types: X Screen, GPU.

  Attribute 'GPUErrors' (air:0.0): 0.
    'GPUErrors' is an integer attribute.
    'GPUErrors' is a read-only attribute.
    'GPUErrors' can use the following target types: X Screen.

  Attribute 'GPUPowerSource' (air:0.0): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfMode' (air:0.0): 1.
    'GPUCurrentPerfMode' is an integer attribute.
    'GPUCurrentPerfMode' is a read-only attribute.
    'GPUCurrentPerfMode' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfLevel' (air:0.0): 3.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen, GPU.

  Attribute 'GPUAdaptiveClockState' (air:0.0): 1.
    'GPUAdaptiveClockState' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen, GPU.

  Attribute 'GPUPerfModes' (air:0.0): perf=0, nvclock=405, memclock=1064, processorclock=405 ; perf=1, nvclock=450, memclock=1064, processorclock=810 ; perf=2, nvclock=450, memclock=1064, processorclock=810 ;
  perf=3, nvclock=450, memclock=1064, processorclock=950 
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen, GPU.

  Attribute 'ECCSupported' (air:0.0): 0.
    'ECCSupported' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'ECCSupported' is a read-only attribute.
    'ECCSupported' can use the following target types: X Screen, GPU.

  Attribute 'ECCConfigurationSupported' (air:0.0): 0.
    'ECCConfigurationSupported' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'ECCConfigurationSupported' is a read-only attribute.
    'ECCConfigurationSupported' can use the following target types: X Screen, GPU.

  Attribute 'GvoSupported' (air:0.0): 0.
    'GvoSupported' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GvoSupported' is a read-only attribute.
    'GvoSupported' can use the following target types: X Screen.

  Attribute 'IsGvoDisplay' (air:0.0; display device: DFP-1): 0.
    'IsGvoDisplay' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'IsGvoDisplay' is a read-only attribute.
    'IsGvoDisplay' is display device specific.
    'IsGvoDisplay' can use the following target types: X Screen, GPU.

  Attribute 'IsGvoDisplay' (air:0.0; display device: DFP-2): 0.
    'IsGvoDisplay' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'IsGvoDisplay' is a read-only attribute.
    'IsGvoDisplay' is display device specific.
    'IsGvoDisplay' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (air:0.0; display device: DFP-1): 0.
    The valid values for 'DigitalVibrance' are in the range -1024 - 1023 (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (air:0.0; display device: DFP-2): 0.
    The valid values for 'DigitalVibrance' are in the range -1024 - 1023 (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'FrontendResolution' (air:0.0; display device: DFP-1): 1920,1080.
    'FrontendResolution' is a packed integer attribute.
    'FrontendResolution' is a read-only attribute.
    'FrontendResolution' is display device specific.
    'FrontendResolution' can use the following target types: X Screen, GPU.

  Attribute 'FrontendResolution' (air:0.0; display device: DFP-2): 1440,900.
    'FrontendResolution' is a packed integer attribute.
    'FrontendResolution' is a read-only attribute.
    'FrontendResolution' is display device specific.
    'FrontendResolution' can use the following target types: X Screen, GPU.

  Attribute 'BackendResolution' (air:0.0; display device: DFP-1): 1920,1080.
    'BackendResolution' is a packed integer attribute.
    'BackendResolution' is a read-only attribute.
    'BackendResolution' is display device specific.
    'BackendResolution' can use the following target types: X Screen, GPU.

  Attribute 'BackendResolution' (air:0.0; display device: DFP-2): 1440,900.
    'BackendResolution' is a packed integer attribute.
    'BackendResolution' is a read-only attribute.
    'BackendResolution' is display device specific.
    'BackendResolution' can use the following target types: X Screen, GPU.

  Attribute 'FlatpanelNativeResolution' (air:0.0; display device: DFP-1): 1920,1080.
    'FlatpanelNativeResolution' is a packed integer attribute.
    'FlatpanelNativeResolution' is a read-only attribute.
    'FlatpanelNativeResolution' is display device specific.
    'FlatpanelNativeResolution' can use the following target types: X Screen, GPU.

  Attribute 'FlatpanelNativeResolution' (air:0.0; display device: DFP-2): 1440,900.
    'FlatpanelNativeResolution' is a packed integer attribute.
    'FlatpanelNativeResolution' is a read-only attribute.
    'FlatpanelNativeResolution' is display device specific.
    'FlatpanelNativeResolution' can use the following target types: X Screen, GPU.

  Attribute 'FlatpanelBestFitResolution' (air:0.0; display device: DFP-1): 1920,1080.
    'FlatpanelBestFitResolution' is a packed integer attribute.
    'FlatpanelBestFitResolution' is a read-only attribute.
    'FlatpanelBestFitResolution' is display device specific.
    'FlatpanelBestFitResolution' can use the following target types: X Screen, GPU.

  Attribute 'FlatpanelBestFitResolution' (air:0.0; display device: DFP-2): 1440,900.
    'FlatpanelBestFitResolution' is a packed integer attribute.
    'FlatpanelBestFitResolution' is a read-only attribute.
    'FlatpanelBestFitResolution' is display device specific.
    'FlatpanelBestFitResolution' can use the following target types: X Screen, GPU.

  Attribute 'DFPScalingActive' (air:0.0; display device: DFP-1): 0.
    'DFPScalingActive' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'DFPScalingActive' is a read-only attribute.
    'DFPScalingActive' is display device specific.
    'DFPScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'DFPScalingActive' (air:0.0; display device: DFP-2): 0.
    'DFPScalingActive' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'DFPScalingActive' is a read-only attribute.
    'DFPScalingActive' is display device specific.
    'DFPScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'GPUScaling' (air:0.0; display device: DFP-1): 2,1.
    Valid values for 'GPUScaling' are: [1 and 2], [1, 2 and 3].
    'GPUScaling' is display device specific.
    'GPUScaling' can use the following target types: X Screen, GPU.

  Attribute 'GPUScaling' (air:0.0; display device: DFP-2): 2,1.
    Valid values for 'GPUScaling' are: [1 and 2], [1, 2 and 3].
    'GPUScaling' is display device specific.
    'GPUScaling' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingDefaultTarget' (air:0.0; display device: DFP-1): 2.
    'GPUScalingDefaultTarget' is an integer attribute.
    'GPUScalingDefaultTarget' is a read-only attribute.
    'GPUScalingDefaultTarget' is display device specific.
    'GPUScalingDefaultTarget' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingDefaultTarget' (air:0.0; display device: DFP-2): 2.
    'GPUScalingDefaultTarget' is an integer attribute.
    'GPUScalingDefaultTarget' is a read-only attribute.
    'GPUScalingDefaultTarget' is display device specific.
    'GPUScalingDefaultTarget' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingDefaultMethod' (air:0.0; display device: DFP-1): 1.
    'GPUScalingDefaultMethod' is an integer attribute.
    'GPUScalingDefaultMethod' is a read-only attribute.
    'GPUScalingDefaultMethod' is display device specific.
    'GPUScalingDefaultMethod' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingDefaultMethod' (air:0.0; display device: DFP-2): 1.
    'GPUScalingDefaultMethod' is an integer attribute.
    'GPUScalingDefaultMethod' is a read-only attribute.
    'GPUScalingDefaultMethod' is display device specific.
    'GPUScalingDefaultMethod' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingActive' (air:0.0; display device: DFP-1): 0.
    'GPUScalingActive' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GPUScalingActive' is a read-only attribute.
    'GPUScalingActive' is display device specific.
    'GPUScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingActive' (air:0.0; display device: DFP-2): 0.
    'GPUScalingActive' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GPUScalingActive' is a read-only attribute.
    'GPUScalingActive' is display device specific.
    'GPUScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (air:0.0; display device: DFP-1): 60,00 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (air:0.0; display device: DFP-2): 59,84 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (air:0.0; display device: DFP-1): 60,000 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (air:0.0; display device: DFP-2): 59,840 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'OverscanCompensation' (air:0.0; display device: DFP-1): 0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200 (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen, GPU.

  Attribute 'OverscanCompensation' (air:0.0; display device: DFP-2): 0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200 (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen, GPU.

  Attribute 'ColorSpace' (air:0.0; display device: DFP-1): 0.
    Valid values for 'ColorSpace' are: 0.
    'ColorSpace' is display device specific.
    'ColorSpace' can use the following target types: X Screen, GPU.

  Attribute 'ColorSpace' (air:0.0; display device: DFP-2): 0.
    Valid values for 'ColorSpace' are: 0.
    'ColorSpace' is display device specific.
    'ColorSpace' can use the following target types: X Screen, GPU.

  Attribute 'ColorRange' (air:0.0; display device: DFP-1): 0.
    Valid values for 'ColorRange' are: 0 and 1.
    'ColorRange' is display device specific.
    'ColorRange' can use the following target types: X Screen, GPU.

  Attribute 'ColorRange' (air:0.0; display device: DFP-2): 0.
    Valid values for 'ColorRange' are: 0 and 1.
    'ColorRange' is display device specific.
    'ColorRange' can use the following target types: X Screen, GPU.

  Attribute 'XVideoTextureBrightness' (air:0.0): 0.
    The valid values for 'XVideoTextureBrightness' are in the range -1000 - 1000 (inclusive).
    'XVideoTextureBrightness' can use the following target types: X Screen.

  Attribute 'XVideoTextureContrast' (air:0.0): 0.
    The valid values for 'XVideoTextureContrast' are in the range -1000 - 1000 (inclusive).
    'XVideoTextureContrast' can use the following target types: X Screen.

  Attribute 'XVideoTextureHue' (air:0.0): 0.
    The valid values for 'XVideoTextureHue' are in the range -1000 - 1000 (inclusive).
    'XVideoTextureHue' can use the following target types: X Screen.

  Attribute 'XVideoTextureSaturation' (air:0.0): 0.
    The valid values for 'XVideoTextureSaturation' are in the range -1000 - 1000 (inclusive).
    'XVideoTextureSaturation' can use the following target types: X Screen.

  Attribute 'XVideoTextureSyncToVBlank' (air:0.0): 1.
    The valid values for 'XVideoTextureSyncToVBlank' are in the range 0 - 1 (inclusive).
    'XVideoTextureSyncToVBlank' can use the following target types: X Screen.

  Attribute 'XVideoSyncToDisplay' (air:0.0): 0x00020000.
    'XVideoSyncToDisplay' is a bitmask attribute.
    'XVideoSyncToDisplay' can use the following target types: X Screen.

Attributes queryable via air:0[gpu:0]:

  Attribute 'OperatingSystem' (air:0[gpu:0]): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2 (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (air:0[gpu:0]): 270.41.06 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen, GPU.

  Attribute 'ConnectedDisplays' (air:0[gpu:0]): 0x00060000.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (air:0[gpu:0]): 0x00060000.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'NotebookInternalLCD' (air:0[gpu:0]): 0x00040000.
    'NotebookInternalLCD' is a bitmask attribute.
    'NotebookInternalLCD' is a read-only attribute.
    'NotebookInternalLCD' can use the following target types: X Screen, GPU.

  Attribute 'Depth30Allowed' (air:0[gpu:0]): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

  Attribute 'NoScanout' (air:0[gpu:0]): 0.
    'NoScanout' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'NoScanout' is a read-only attribute.
    'NoScanout' can use the following target types: X Screen, GPU.

  Attribute 'SliMosaicModeAvailable' (air:0[gpu:0]): 0.
    'SliMosaicModeAvailable' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'SliMosaicModeAvailable' is a read-only attribute.
    'SliMosaicModeAvailable' can use the following target types: X Screen, GPU, VCS.

  Attribute 'BusType' (air:0[gpu:0]): 3.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU, SDI Input Device.

  Attribute 'VideoRam' (air:0[gpu:0]): 262144.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.

  Attribute 'Irq' (air:0[gpu:0]): 16.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU, SDI Input Device.

  Attribute 'CUDACores' (air:0[gpu:0]): 48.
    'CUDACores' is an integer attribute.
    'CUDACores' is a read-only attribute.
    'CUDACores' can use the following target types: X Screen, GPU.

  Attribute 'GPUMemoryInterface' (air:0[gpu:0]): 128.
    'GPUMemoryInterface' is an integer attribute.
    'GPUMemoryInterface' is a read-only attribute.
    'GPUMemoryInterface' can use the following target types: X Screen, GPU.

  Attribute 'GPUCoreTemp' (air:0[gpu:0]): 67.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

  Attribute 'GPU2DClockFreqs' (air:0[gpu:0]): 405,1064.
    The valid values for 'GPU2DClockFreqs' are in the ranges 101 - 810, 266 - 1276 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPU3DClockFreqs' (air:0[gpu:0]): 450,1064.
    The valid values for 'GPU3DClockFreqs' are in the ranges 112 - 900, 266 - 1276 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault2DClockFreqs' (air:0[gpu:0]): 405,1064.
    'GPUDefault2DClockFreqs' is a packed integer attribute.
    'GPUDefault2DClockFreqs' is a read-only attribute.
    'GPUDefault2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault3DClockFreqs' (air:0[gpu:0]): 450,1064.
    'GPUDefault3DClockFreqs' is a packed integer attribute.
    'GPUDefault3DClockFreqs' is a read-only attribute.
    'GPUDefault3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentClockFreqs' (air:0[gpu:0]): 450,1064.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentProcessorClockFreqs' (air:0[gpu:0]): 950.
    The valid values for 'GPUCurrentProcessorClockFreqs' are in the range 237 - 1900 (inclusive).
    'GPUCurrentProcessorClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentClockFreqsString' (air:0[gpu:0]): nvclock=450, memclock=1064, processorclock=950 
    'GPUCurrentClockFreqsString' is a string attribute.
    'GPUCurrentClockFreqsString' can use the following target types: X Screen, GPU.

  Attribute 'PCIDomain' (air:0[gpu:0]): 0.
    'PCIDomain' is an integer attribute.
    'PCIDomain' is a read-only attribute.
    'PCIDomain' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIBus' (air:0[gpu:0]): 2.
    'PCIBus' is an integer attribute.
    'PCIBus' is a read-only attribute.
    'PCIBus' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIDevice' (air:0[gpu:0]): 0.
    'PCIDevice' is an integer attribute.
    'PCIDevice' is a read-only attribute.
    'PCIDevice' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIFunc' (air:0[gpu:0]): 0.
    'PCIFunc' is an integer attribute.
    'PCIFunc' is a read-only attribute.
    'PCIFunc' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIID' (air:0[gpu:0]): 4318,2211.
    'PCIID' is a packed integer attribute.
    'PCIID' is a read-only attribute.
    'PCIID' can use the following target types: GPU, SDI Input Device.

  Attribute 'GPUPowerSource' (air:0[gpu:0]): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfMode' (air:0[gpu:0]): 1.
    'GPUCurrentPerfMode' is an integer attribute.
    'GPUCurrentPerfMode' is a read-only attribute.
    'GPUCurrentPerfMode' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfLevel' (air:0[gpu:0]): 3.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen, GPU.

  Attribute 'GPUAdaptiveClockState' (air:0[gpu:0]): 1.
    'GPUAdaptiveClockState' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen, GPU.

  Attribute 'GPUPerfModes' (air:0[gpu:0]): perf=0, nvclock=405, memclock=1064, processorclock=405 ; perf=1, nvclock=450, memclock=1064, processorclock=810 ; perf=2, nvclock=450, memclock=1064,
  processorclock=810 ; perf=3, nvclock=450, memclock=1064, processorclock=950 
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen, GPU.

  Attribute 'GPUPowerMizerMode' (air:0[gpu:0]): 0.
    'GPUPowerMizerMode' is an integer attribute.
    'GPUPowerMizerMode' can use the following target types: GPU.

  Attribute 'ECCSupported' (air:0[gpu:0]): 0.
    'ECCSupported' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'ECCSupported' is a read-only attribute.
    'ECCSupported' can use the following target types: X Screen, GPU.

  Attribute 'ECCConfigurationSupported' (air:0[gpu:0]): 0.
    'ECCConfigurationSupported' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'ECCConfigurationSupported' is a read-only attribute.
    'ECCConfigurationSupported' can use the following target types: X Screen, GPU.

  Attribute 'IsGvoDisplay' (air:0[gpu:0]; display device: DFP-1): 0.
    'IsGvoDisplay' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'IsGvoDisplay' is a read-only attribute.
    'IsGvoDisplay' is display device specific.
    'IsGvoDisplay' can use the following target types: X Screen, GPU.

  Attribute 'IsGvoDisplay' (air:0[gpu:0]; display device: DFP-2): 0.
    'IsGvoDisplay' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'IsGvoDisplay' is a read-only attribute.
    'IsGvoDisplay' is display device specific.
    'IsGvoDisplay' can use the following target types: X Screen, GPU.

  Attribute 'Dithering' (air:0[gpu:0]; display device: DFP-1): 0.
    'Dithering' is an integer attribute.
    'Dithering' is display device specific.
    'Dithering' can use the following target types: GPU.

  Attribute 'Dithering' (air:0[gpu:0]; display device: DFP-2): 1.
    'Dithering' is an integer attribute.
    'Dithering' is display device specific.
    'Dithering' can use the following target types: GPU.

  Attribute 'CurrentDithering' (air:0[gpu:0]; display device: DFP-1): 0.
    'CurrentDithering' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'CurrentDithering' is a read-only attribute.
    'CurrentDithering' is display device specific.
    'CurrentDithering' can use the following target types: GPU.

  Attribute 'CurrentDithering' (air:0[gpu:0]; display device: DFP-2): 1.
    'CurrentDithering' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'CurrentDithering' is a read-only attribute.
    'CurrentDithering' is display device specific.
    'CurrentDithering' can use the following target types: GPU.

  Attribute 'DitheringMode' (air:0[gpu:0]; display device: DFP-1): 0.
    Valid values for 'DitheringMode' are: 0, 1 and 2.
    'DitheringMode' is display device specific.
    'DitheringMode' can use the following target types: GPU.

  Attribute 'DitheringMode' (air:0[gpu:0]; display device: DFP-2): 0.
    Valid values for 'DitheringMode' are: 0, 1 and 2.
    'DitheringMode' is display device specific.
    'DitheringMode' can use the following target types: GPU.

  Attribute 'CurrentDitheringMode' (air:0[gpu:0]; display device: DFP-1): 0.
    'CurrentDitheringMode' is an integer attribute.
    'CurrentDitheringMode' is a read-only attribute.
    'CurrentDitheringMode' is display device specific.
    'CurrentDitheringMode' can use the following target types: GPU.

  Attribute 'CurrentDitheringMode' (air:0[gpu:0]; display device: DFP-2): 1.
    'CurrentDitheringMode' is an integer attribute.
    'CurrentDitheringMode' is a read-only attribute.
    'CurrentDitheringMode' is display device specific.
    'CurrentDitheringMode' can use the following target types: GPU.

  Attribute 'DitheringDepth' (air:0[gpu:0]; display device: DFP-1): 0.
    'DitheringDepth' is an integer attribute.
    'DitheringDepth' is display device specific.
    'DitheringDepth' can use the following target types: GPU.

  Attribute 'DitheringDepth' (air:0[gpu:0]; display device: DFP-2): 1.
    'DitheringDepth' is an integer attribute.
    'DitheringDepth' is display device specific.
    'DitheringDepth' can use the following target types: GPU.

  Attribute 'CurrentDitheringDepth' (air:0[gpu:0]; display device: DFP-1): 0.
    'CurrentDitheringDepth' is an integer attribute.
    'CurrentDitheringDepth' is a read-only attribute.
    'CurrentDitheringDepth' is display device specific.
    'CurrentDitheringDepth' can use the following target types: GPU.

  Attribute 'CurrentDitheringDepth' (air:0[gpu:0]; display device: DFP-2): 1.
    'CurrentDitheringDepth' is an integer attribute.
    'CurrentDitheringDepth' is a read-only attribute.
    'CurrentDitheringDepth' is display device specific.
    'CurrentDitheringDepth' can use the following target types: GPU.

  Attribute 'DigitalVibrance' (air:0[gpu:0]; display device: DFP-1): 0.
    The valid values for 'DigitalVibrance' are in the range -1024 - 1023 (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (air:0[gpu:0]; display device: DFP-2): 0.
    The valid values for 'DigitalVibrance' are in the range -1024 - 1023 (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'FrontendResolution' (air:0[gpu:0]; display device: DFP-1): 1920,1080.
    'FrontendResolution' is a packed integer attribute.
    'FrontendResolution' is a read-only attribute.
    'FrontendResolution' is display device specific.
    'FrontendResolution' can use the following target types: X Screen, GPU.

  Attribute 'FrontendResolution' (air:0[gpu:0]; display device: DFP-2): 1440,900.
    'FrontendResolution' is a packed integer attribute.
    'FrontendResolution' is a read-only attribute.
    'FrontendResolution' is display device specific.
    'FrontendResolution' can use the following target types: X Screen, GPU.

  Attribute 'BackendResolution' (air:0[gpu:0]; display device: DFP-1): 1920,1080.
    'BackendResolution' is a packed integer attribute.
    'BackendResolution' is a read-only attribute.
    'BackendResolution' is display device specific.
    'BackendResolution' can use the following target types: X Screen, GPU.

  Attribute 'BackendResolution' (air:0[gpu:0]; display device: DFP-2): 1440,900.
    'BackendResolution' is a packed integer attribute.
    'BackendResolution' is a read-only attribute.
    'BackendResolution' is display device specific.
    'BackendResolution' can use the following target types: X Screen, GPU.

  Attribute 'FlatpanelNativeResolution' (air:0[gpu:0]; display device: DFP-1): 1920,1080.
    'FlatpanelNativeResolution' is a packed integer attribute.
    'FlatpanelNativeResolution' is a read-only attribute.
    'FlatpanelNativeResolution' is display device specific.
    'FlatpanelNativeResolution' can use the following target types: X Screen, GPU.

  Attribute 'FlatpanelNativeResolution' (air:0[gpu:0]; display device: DFP-2): 1440,900.
    'FlatpanelNativeResolution' is a packed integer attribute.
    'FlatpanelNativeResolution' is a read-only attribute.
    'FlatpanelNativeResolution' is display device specific.
    'FlatpanelNativeResolution' can use the following target types: X Screen, GPU.

  Attribute 'FlatpanelBestFitResolution' (air:0[gpu:0]; display device: DFP-1): 1920,1080.
    'FlatpanelBestFitResolution' is a packed integer attribute.
    'FlatpanelBestFitResolution' is a read-only attribute.
    'FlatpanelBestFitResolution' is display device specific.
    'FlatpanelBestFitResolution' can use the following target types: X Screen, GPU.

  Attribute 'FlatpanelBestFitResolution' (air:0[gpu:0]; display device: DFP-2): 1440,900.
    'FlatpanelBestFitResolution' is a packed integer attribute.
    'FlatpanelBestFitResolution' is a read-only attribute.
    'FlatpanelBestFitResolution' is display device specific.
    'FlatpanelBestFitResolution' can use the following target types: X Screen, GPU.

  Attribute 'DFPScalingActive' (air:0[gpu:0]; display device: DFP-1): 0.
    'DFPScalingActive' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'DFPScalingActive' is a read-only attribute.
    'DFPScalingActive' is display device specific.
    'DFPScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'DFPScalingActive' (air:0[gpu:0]; display device: DFP-2): 0.
    'DFPScalingActive' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'DFPScalingActive' is a read-only attribute.
    'DFPScalingActive' is display device specific.
    'DFPScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'GPUScaling' (air:0[gpu:0]; display device: DFP-1): 2,1.
    Valid values for 'GPUScaling' are: [1 and 2], [1, 2 and 3].
    'GPUScaling' is display device specific.
    'GPUScaling' can use the following target types: X Screen, GPU.

  Attribute 'GPUScaling' (air:0[gpu:0]; display device: DFP-2): 2,1.
    Valid values for 'GPUScaling' are: [1 and 2], [1, 2 and 3].
    'GPUScaling' is display device specific.
    'GPUScaling' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingDefaultTarget' (air:0[gpu:0]; display device: DFP-1): 2.
    'GPUScalingDefaultTarget' is an integer attribute.
    'GPUScalingDefaultTarget' is a read-only attribute.
    'GPUScalingDefaultTarget' is display device specific.
    'GPUScalingDefaultTarget' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingDefaultTarget' (air:0[gpu:0]; display device: DFP-2): 2.
    'GPUScalingDefaultTarget' is an integer attribute.
    'GPUScalingDefaultTarget' is a read-only attribute.
    'GPUScalingDefaultTarget' is display device specific.
    'GPUScalingDefaultTarget' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingDefaultMethod' (air:0[gpu:0]; display device: DFP-1): 1.
    'GPUScalingDefaultMethod' is an integer attribute.
    'GPUScalingDefaultMethod' is a read-only attribute.
    'GPUScalingDefaultMethod' is display device specific.
    'GPUScalingDefaultMethod' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingDefaultMethod' (air:0[gpu:0]; display device: DFP-2): 1.
    'GPUScalingDefaultMethod' is an integer attribute.
    'GPUScalingDefaultMethod' is a read-only attribute.
    'GPUScalingDefaultMethod' is display device specific.
    'GPUScalingDefaultMethod' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingActive' (air:0[gpu:0]; display device: DFP-1): 0.
    'GPUScalingActive' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GPUScalingActive' is a read-only attribute.
    'GPUScalingActive' is display device specific.
    'GPUScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingActive' (air:0[gpu:0]; display device: DFP-2): 0.
    'GPUScalingActive' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GPUScalingActive' is a read-only attribute.
    'GPUScalingActive' is display device specific.
    'GPUScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (air:0[gpu:0]; display device: DFP-1): 60,00 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (air:0[gpu:0]; display device: DFP-2): 59,84 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (air:0[gpu:0]; display device: DFP-1): 60,000 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (air:0[gpu:0]; display device: DFP-2): 59,840 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'OverscanCompensation' (air:0[gpu:0]; display device: DFP-1): 0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200 (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen, GPU.

  Attribute 'OverscanCompensation' (air:0[gpu:0]; display device: DFP-2): 0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200 (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen, GPU.

  Attribute 'ColorSpace' (air:0[gpu:0]; display device: DFP-1): 0.
    Valid values for 'ColorSpace' are: 0.
    'ColorSpace' is display device specific.
    'ColorSpace' can use the following target types: X Screen, GPU.

  Attribute 'ColorSpace' (air:0[gpu:0]; display device: DFP-2): 0.
    Valid values for 'ColorSpace' are: 0.
    'ColorSpace' is display device specific.
    'ColorSpace' can use the following target types: X Screen, GPU.

  Attribute 'ColorRange' (air:0[gpu:0]; display device: DFP-1): 0.
    Valid values for 'ColorRange' are: 0 and 1.
    'ColorRange' is display device specific.
    'ColorRange' can use the following target types: X Screen, GPU.

  Attribute 'ColorRange' (air:0[gpu:0]; display device: DFP-2): 0.
    Valid values for 'ColorRange' are: 0 and 1.
    'ColorRange' is display device specific.
    'ColorRange' can use the following target types: X Screen, GPU.

  Attribute 'SynchronousPaletteUpdates' (air:0[gpu:0]; display device: DFP-1): 0.
    'SynchronousPaletteUpdates' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'SynchronousPaletteUpdates' is display device specific.
    'SynchronousPaletteUpdates' can use the following target types: GPU.

  Attribute 'SynchronousPaletteUpdates' (air:0[gpu:0]; display device: DFP-2): 0.
    'SynchronousPaletteUpdates' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'SynchronousPaletteUpdates' is display device specific.
    'SynchronousPaletteUpdates' can use the following target types: GPU.

Attributes queryable via air:0[thermalsensor:0]:

  Attribute 'ThermalSensorReading' (air:0[thermalsensor:0]): 67.
    The valid values for 'ThermalSensorReading' are in the range 0 - 127 (inclusive).
    'ThermalSensorReading' is a read-only attribute.
    'ThermalSensorReading' can use the following target types: Thermal Sensor.

  Attribute 'ThermalSensorProvider' (air:0[thermalsensor:0]): 1.
    'ThermalSensorProvider' is an integer attribute.
    'ThermalSensorProvider' is a read-only attribute.
    'ThermalSensorProvider' can use the following target types: Thermal Sensor.

  Attribute 'ThermalSensorTarget' (air:0[thermalsensor:0]): 1.
    'ThermalSensorTarget' is an integer attribute.
    'ThermalSensorTarget' is a read-only attribute.
    'ThermalSensorTarget' can use the following target types: Thermal Sensor.

```

---

### Post by tjones00 on 2011-08-04
That is a tall order however you can probably sort it out with the following references.

[http://wiki.bash-hackers.org/start](http://wiki.bash-hackers.org/start)

```

brawndo@brawndo:~$ nvidia-xconfig -A

nvidia-xconfig:  version 270.41.06 
(buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT
2011
  The NVIDIA X Configuration Tool.

  This program is used to manipulate X configuration files, specifically to
  enable NVIDIA X driver functionality.

  Copyright (C) 2005 - 2010 NVIDIA Corporation.


  In its normal operation, nvidia-xconfig finds the system X configuration file
  (or generates a new X configuration if it cannot find the system file), makes
  sure the configuration is usable by the NVIDIA X driver, applies any updates
  requested on the commandline, and writes the new configuration to file.

  Please see the NVIDIA README for a description of NVIDIA X configuration file
  options.


nvidia-xconfig [options]

  -c XCONFIG, --xconfig=XCONFIG
      Use XCONFIG as the input X config file; if this option is not specified,
      then the same search path used by the X server will be used to find the X
      configuration file.

  -o OUTPUT-XCONFIG, --output-xconfig=OUTPUT-XCONFIG
      Use OUTPUT-XCONFIG as the output X configuration file; if this option is
      not specified, then the input X configuration filename will also be used
      as the output X configuration filename.

  -s, --silent
      Run silently; no messages will be printed to stdout, except for warning
      and error messages to stderr.

  -t, --tree
      Read the X configuration file, print to stdout the X configuration data
      in a tree format, and exit.

  -v, --version
      Print the nvidia-xconfig version and exit.

  -h, --help
      Print usage information for the common commandline options and exit.

  -A, --advanced-help
      Print usage information for the common commandline options as well as the
      advanced options, and then exit.

  --acpid-socket-path=ACPID-SOCKET-PATH, --no-acpid-socket-path
      Set this option to specify an alternate path to the Linux ACPI daemon
      (acpid)'s socket, which the NVIDIA X driver will use to connect to
      acpid.

  --add-argb-glx-visuals, --no-add-argb-glx-visuals
      Enables or disables support for OpenGL rendering into 32-bit ARGB windows
      and pixmaps.

  --allow-glx-with-composite, --no-allow-glx-with-composite
      Enable or disable the "AllowGLXWithComposite" X configuration option.

  --bandwidth-test, --no-bandwidth-test
      Disable or enable the "NoBandWidthTest" X configuration option.

  --busid=BUSID, --no-busid
      This option writes the specified BusID to the device section of the X
      configuration file.  If there are multiple device sections, then it adds
      the BusID field to each of them.  To add the BusID to only a specific
      device or screen section, use the '--device' or '--screen' options.

  --preserve-busid, --no-preserve-busid
      By default, nvidia-xconfig preserves the existing BusID in the X
      configuration file only if there are multiple X screens configured for
      the X server.  Use '--preserve-busid' or '--no-preserve-busid' to force
      the BusID to be preserved or not preserved, overriding the default
      behavior.

  --cool-bits=COOL-BITS, --no-cool-bits
      Enable or disable the "Coolbits" X configuration option.  Setting this
      option will enable support in the NV-CONTROL X extension for manipulating
      GPU clock and GPU fan control settings. Default value is 0.  For fan
      control set it to 4.  WARNING: this may cause system damage and void
      warranties.

  --composite, --no-composite
      Enable or disable the "Composite" X extension.

  --connected-monitor=CONNECTED-MONITOR, --no-connected-monitor
      Enable or disable the  "ConnectedMonitor" X configuration option; setting
      this option forces the X driver to behave as if the specified display
      devices are connected to the GPU.

  --connect-to-acpid, --no-connect-to-acpid
      Enable or disable the "ConnectToAcpid" X configuration option.  If this
      option is set, the NVIDIA X driver will attempt to connect to the Linux
      ACPI daemon (acpid).  Set this option to off to prevent the X driver from
      attempting to connect to acpid.

  --constant-dpi, --no-constant-dpi
      Enable or disable the "ConstantDPI" X configuration option, which
      controls whether the NVIDIA X driver maintains a constant dots per inch
      (DPI) value by recomputing the reported size in millimeters of the X
      screen when XRandR changes the size in pixels of the X screen.

  --custom-edid=CUSTOM-EDID, --no-custom-edid
      Enable or disable the  "CustomEDID" X configuration option; setting this
      option forces the X driver to use the EDID specified.This option is a
      semicolon-separated list of pairs of display device names and filename
      pairs; e.g "CRT-0:\tmp\edid.bin". Note that a display device name must
      always be specified even if only one EDID is specified. 

  --dac-8bit, --no-dac-8bit
      Most Quadro parts by default use a 10 bit color look up table (LUT) by
      default; setting this option to TRUE forces these graphics chips to use
      an 8 bit (LUT).

  -d DEPTH, --depth=DEPTH
      Set the default depth to DEPTH; valid values for DEPTH are 8, 15, 16, 24,
      and 30.

  --device=DEVICE
      The nvidia-xconfig utility operates on one or more devices in the X
      configuration file.  If this option is specified, the device named DEVICE
      in the X configuration file will be used.  If this option is not
      specified, all the devices within the X configuration file will be used.

  --disable-glx-root-clipping, --no-disable-glx-root-clipping
      Disable or enable clipping OpenGL rendering to the root window via the
      "DisableGLXRootClipping" X configuration option.

  --damage-events, --no-damage-events
      Use OS-level events to notify the X server when a direct-rendering client
      has performed rendering that needs to be composited to the screen. 
      Improves performance when using GLX with the composite extension.

  --dynamic-twinview, --no-dynamic-twinview
      Enable or disable support for dynamically configuring TwinView.

  --preserve-driver-name
      By default nvidia-xconfig changes the  display  driver  to "nvidia" for
      all configured X screens; this option preserves the existing driver name
      of each X screen.

  --enable-acpi-hotkeys, --no-enable-acpi-hotkeys
      The "EnableACPIHotkeys" option can be specified to override the NVIDIA X
      driver's default decision to enable or disable ACPI display change hotkey
      events.

  -a, --enable-all-gpus
      Configure an X screen on every GPU in the system.

  --exact-mode-timings-dvi, --no-exact-mode-timings-dvi
      Forces the initialization of the X server with the exact timings
      specified in the ModeLine.

  -E FILE, --extract-edids-from-file=FILE
      Extract any raw EDID byte blocks contained in the specified X log file
      LOG; raw EDID bytes are printed by the NVIDIA X driver to the X log as
      hexidecimal when verbose logging is enabled with the "-logverbose 6" X
      server commandline option.  Any extracted EDIDs are then written as
      binary data to individual files.  These files can later be used by the
      NVIDIA X driver through the "CustomEDID" X configuration option.

  --extract-edids-output-file=FILENAME
      When the '--extract-edids-from-file' option is used, nvidia-xconfig
      writes any extracted EDID to a file, typically "edid.bin" in the current
      directory.  Use this option to specify an alternate filename.  Note that
      nvidia-xconfig, if necessary, will append a unique number to the EDID
      filename, to avoid overwriting existing files (e.g., "edid.bin.1" if
      "edid.bin" already exists).

  --flatpanel-properties=FLATPANEL-PROPERTIES, --no-flatpanel-properties
      Set the flat panel properties. The supported properties are: 'scaling',
      'dithering' & 'ditheringmode'.  Please see the NVIDIA README 'Appendix B.
      X Config Options' for more details on the possible values and syntax.

  --flip, --no-flip
      Enable or disable OpenGL flipping

  --force-generate
      Force generation of a new X config file, ignoring any existing system X
      config file.  This is not typically recommended, as things like the mouse
      protocol, keyboard layout, font paths, etc, are setup by your Unix
      distribution.  While nvidia-xconfig can attempt to infer these values, it
      is best to use your Unix distribution's X config file for the basis of
      anything that nvidia-xconfig creates.

  --force-stereo-flipping, --no-force-stereo-flipping
      Normally, stereo flipping is only performed when a stereo drawable is
      visible. This option forces stereo flipping even when no stereo drawables
      are visible.

  --handle-special-keys=WHEN, --no-handle-special-keys
      Specify when the X server should use the builtin keyboard handler to
      process special key combinations (such as Ctrl+Alt+Backspace); see the X
      configuration man page for details.  The value of WHEN can be 'Always',
      'Never', or 'WhenNeeded'.

  --include-implicit-metamodes, --no-include-implicit-metamodes
      Enable or disable the "IncludeImplicitMetaModes" X configuration option.

  --keyboard=KEYBOARD
      When generating a new X configuration file (which happens when no system
      X configuration file can be found, or the '--force-generate' option is
      specified), use KEYBOARD as the keyboard type, rather than attempting to
      probe the system for the keyboard type.  For a list of possible keyboard
      types, see the '--keyboard-list' option.

  --keyboard-driver=DRIVER
      In most cases nvidia-xconfig can automatically determine the correct
      keyboard driver to use (either 'kbd' or 'keyboard'). Use this option to
      override what nvidia-xconfig detects. Typically, if you are using an
      X.Org X server, use 'kdb'; if you are using an XFree86 X server, use
      'keyboard'.

  --keyboard-list
      Print to stdout the available keyboard types recognized by the
      '--keyboard' option, and then exit.

  --layout=LAYOUT
      The nvidia-xconfig utility operates on a Server Layout within the X
      configuration file.  If this option is specified, the layout named LAYOUT
      in the X configuration file will be used.  If this option is not
      specified, the first Server Layout in the X configuration file is used.

  --logo, --no-logo
      Disable or enable the "NoLogo" X configuration option.

  --logo-path=PATH, --no-logo-path
      Set the path to the PNG file to be used as the logo splash screen at X
      server startup.

  --mode=MODE
      Add the specified mode to the mode list.

  --mode-debug, --no-mode-debug
      Enable or disable the "ModeDebug" X configuration option; when enabled,
      this option causes the X driver to print verbose details about mode
      validation to the X log file.

  --mode-list=MODELIST
      Remove all existing modes from the X configuration's modelist and add the
      one(s) specified in the MODELIST string.

  --remove-mode=MODE
      Remove the specified mode from the mode list.

  --metamodes=METAMODES
      Add the MetaMode X configuration option with the value METAMODES which
      will replace any existing MetaMode option already in the X configuration
      file.

  --mouse=MOUSE
      When generating a new X configuration file (which happens when no system
      X configuration file can be found, or the '--force-generate' option is
      specified), use MOUSE as the mouse type, rather than attempting to probe
      the system for the mouse type.  For a list of possible mouse types, see
      the '--mouse-list' option.

  --mouse-list
      Print to stdout the available mouse types recognized by the '--mouse'
      option, and then exit.

  --multigpu=MULTIGPU, --no-multigpu
      Enable or disable MultiGPU.  Valid values for MULTIGPU are 'Off', 'On',
      'Auto', 'AFR', 'SFR', 'AA'.

  --multisample-compatibility, --no-multisample-compatibility
      Enable or disable the use of separate front and back multisample
      buffers.

  --nvagp=NVAGP, --no-nvagp
      Set the NvAGP X config option value.  Possible values are 0 (no AGP), 1
      (NVIDIA's AGP), 2 (AGPGART), 3 (try AGPGART, then try NVIDIA's AGP);
      these values can also be specified as 'none', 'nvagp', 'agpgart', or
      'any'.

  --nvidia-cfg-path=PATH
      The nvidia-cfg library is used to communicate with the NVIDIA kernel
      module to query basic properties of every GPU in the system.  This
      library is typically only used by nvidia-xconfig when configuring
      multiple X screens.  This option tells nvidia-xconfig where to look for
      this library (in case it cannot find it on its own).  This option should
      normally not be needed.

  --only-one-x-screen
      Disable all but one X screen.

  --overlay, --no-overlay
      Enable or disable the "Overlay" X configuration option.

  --cioverlay, --no-cioverlay
      Enable or disable the color index overlay.

  --overlay-default-visual, --no-overlay-default-visual
      Enable or disable the "OverlayDefaultVisual" X configuration option.

  --transparent-index=INDEX, --no-transparent-index
      Pixel to use as transparent when using color index overlays.  Valid
      values for TRANSPARENT-INDEX are 0-255.

  -T, --post-tree
      Like the '--tree' option, but goes through the full process of applying
      any user requested updates to the X configuration, before printing the
      final configuration to stdout in a tree format.  Effectively, this option
      just causes the configuration to be printed to stdout as a tree instead
      of writing the results to file.

  --power-connector-check, --no-power-connector-check
      Disable or enable the "NoPowerConnectorCheck" X configuration option.

  --probe-all-gpus, --no-probe-all-gpus
      Disable or enable the "ProbeAllGpus" X configuration option.

  --query-gpu-info
      Print information about all recognized NVIDIA GPUs in the system.

  --randr-rotation, --no-randr-rotation
      Enable or disable the "RandRRotation" X configuration option.

  --registry-dwords=REGISTRY-DWORDS, --no-registry-dwords
      Enable or disable the "RegistryDwords" X configuration option.

  --render-accel, --no-render-accel
      Enable or disable the "RenderAccel" X configuration option.

  --render-extension, --no-render-extension
      Disable or enable the "NoRenderExtension" X configuration option.

  --rotate=ROTATE, --no-rotate
      Enable or disable the "Rotate" X configuration option.  Valid values for
      ROTATE are 'normal', 'left', 'CCW', 'inverted', 'right', and 'CW'. 
      Rotation can be disabled 

  --screen=SCREEN
      The nvidia-xconfig utility operates on one or more screens within a
      Server Layout in the X configuration file.  If this option is specified,
      the screen named SCREEN in the X configuration file will be used.  If
      this option is not specified, all screens within the selected Server
      Layout in the X configuration file will be used used.

  --separate-x-screens, --no-separate-x-screens
      A GPU that supports multiple simultaneous display devices can either
      drive these display devices in TwinView, or as separate X screens.  When
      the '--separate-x-screens' option is specified, each GPU on which an X
      screen is currently configured will be updated to have two X screens
      configured.  The '--no-separate-x-screens' option will remove the second
      configured X screen on each GPU.  Please see the NVIDIA README
      description of "Separate X Screens on One GPU" for further details.

  --sli=SLI, --no-sli
      Enable or disable SLI.  Valid values for SLI are 'Off', 'On', 'Auto',
      'AFR', 'SFR', 'AA', 'AFRofAA', 'Mosaic'.

  --stereo=STEREO, --no-stereo
      Enable or disable the stereo mode.  Valid values for STEREO are: 0
      (Disabled), 1 (DDC glasses), 2 (Blueline glasses), 3 (Onboard stereo), 4
      (TwinView clone mode stereo), 5 (SeeReal digital flat panel), 6 (Sharp3D
      digital flat panel), 7 (Arisawa/Hyundai/Zalman/Pavione/Miracube), 8 (3D
      DLP), 9 (3D DLP INV), 10 (NVIDIA 3D VISION), 11 (NVIDIA 3D VISION PRO).

  --thermal-configuration-check, --no-thermal-configuration-check
      Disable or enable the "ThermalConfigurationCheck" X configuration
      option.

  --tv-standard=TV-STANDARD, --no-tv-standard
      Enable or disable the "TVStandard" X configuration option. Valid values
      for "TVStandard" are: "PAL-B", "PAL-D", "PAL-G", "PAL-H", "PAL-I",
      "PAL-K1", "PAL-M", "PAL-N", "PAL-NC", "NTSC-J", "NTSC-M", "HD480i",
      "HD480p", "HD720p", "HD1080i", "HD1080p", "HD576i", "HD576p".

  --tv-out-format=TV-OUT-FORMAT, --no-tv-out-format
      Enable or disable the "TVOutFormat" X configuration option. Valid values
      for "TVOutFormat" are: "SVIDEO" and "COMPOSITE".

  --tv-over-scan=TV-OVER-SCAN, --no-tv-over-scan
      Enable or disable the "TVOverScan" X configuration option. Valid values
      are decimal values in the range 1.0 and 0.0.

  --twinview, --no-twinview
      Enable or disable TwinView.

  --twinview-orientation=ORIENTATION, --no-twinview-orientation
      Specify the TwinViewOrientation.  Valid values for ORIENTATION are:
      "RightOf" (the default), "LeftOf", "Above", "Below", or "Clone".

  --twinview-xinerama-info, --no-twinview-xinerama-info
      Prohibits providing Xinerama information when in TwinView.

  --twinview-xinerama-info-order=TWINVIEW-XINERAMA-INFO-ORDER,
  --no-twinview-xinerama-info-order
      Enable or disable the "TwinViewXineramaInfoOrder" X configuration option.
      TWINVIEW-XINERAMA-INFO-ORDER is a comma-separated list of display device
      names that describe the order in which TwinViewXineramaInfo should be
      reported.  E.g., "CRT, DFP, TV".

  --ubb, --no-ubb
      Enable or disable the "UBB" X configuration option.

  --use-edid, --no-use-edid
      Enable or disable use of the EDID (Extended Display Identification Data)
      from your display device(s).  The EDID will be used for driver operations
      such as building lists of available modes, determining valid frequency
      ranges, and computing the DPI (Dots Per Inch).  This option defaults to
      TRUE (the NVIDIA X driver will use the EDID, when available).  It is NOT
      recommended that you use this option to globally disable use of the EDID;
      instead, use '--no-use-edid-freqs' or '--no-use-edid-dpi' to disable
      specific uses of the EDID.

  --use-edid-dpi, --no-use-edid-dpi
      Enable or disable use of the physical size information in the display
      device's EDID, if any, to compute the DPI (Dots Per Inch) of the X
      screen.  This option defaults to TRUE (the NVIDIA X driver uses the
      EDID's physical size, when available, to compute the DPI).

  --use-edid-freqs, --no-use-edid-freqs
      Enable or disable use of the HorizSync and VertRefresh ranges given in a
      display device's EDID, if any.  EDID provided range information will
      override the HorizSync and VertRefresh ranges specified in the Monitor
      section.  This option defaults to TRUE (the NVIDIA X driver will use
      frequency information from the EDID, when available).

  --use-int10-module, --no-use-int10-module
      Enable use of the X Int10 module to soft-boot all secondary cards, rather
      than POSTing the cards through the NVIDIA kernel module.

  --use-display-device=DISPLAY-DEVICE, --no-use-display-device
      Force the X driver to use the display device specified.

  --use-events, --no-use-events
      Enable or disable "UseEvents" X configuration option. Setting this option
      will enable the X driver to use the system events in some cases when it
      is waiting for the hardware. With this option X driver sets an event
      handler and waits for the hardware through the poll() system call. This
      option defaults to FALSE.

  --virtual=WIDTHxHEIGHT, --no-virtual
      Specify the virtual screen resolution.

  --x-prefix=X-PREFIX
      The X installation prefix; the default is /usr/X11R6/.  Only under rare
      circumstances should this option be needed.

  --xinerama, --no-xinerama
      Enable or disable Xinerama.

  --xvmc-uses-textures, --no-xvmc-uses-textures
      Forces XvMC to use the 3D engine for XvMCPutSurface requests rather than
      the video overlay.

  --color-space=COLORSPACE, --no-color-space
      Enable or disable the "ColorSpace" X configuration option. Valid values
      for "COLORSPACE" are: "RGB" and "YCbCr444".

  --color-range=COLORRANGE, --no-color-range
      Sets the "ColorRange" X configuration option. Valid values for
      "COLORRANGE" are: "Full" and "Limited".

  --3dvision-usb-path=3DVISION-USB-PATH
      Set this option to specify the sysfs path of the connected USB dongle.

  --3dvisionpro-config-file=3DVISIONPRO-CONFIG-FILE
      Set this option to specify the NVIDIA 3DVisionPro configuration file.
      Ensure X server has a read and write access permissions to this file.
      NVIDIA X driver stores the hub and the pairing configuration in this file
      to re-use across X restarts. If this option is not provided, 3D VisionPro
      configuration will not be stored.

  --3dvision-display-type=3DVISION-DISPLAY-TYPE, --no-3dvision-display-type
      When NVIDIA 3D Vision is enabled with a non 3D Vision ready display, use
      this option to specify the display type. Valid values are: 0 (Assume it
      is a CRT), 1 (Assume it is a DLP) and 2 (Assume it is a DLP TV and enable
      the checkerboard output).

```

---

### Post by eyerouge on 2011-08-04
Thanks, but  *nvidia-xconfig * writes to the file and also doesn't apply anything without a restart. nvidia-settings GUI does neither and can still handle it all.... now hot to get it done with the commands only, thats the question...

---

### Post by BicyclerBoy on 2011-08-05
nvidia-settings can be used from the command line & the changes can be immediate.

xrandr in conjunction with twinview metamodes or dynamic twinview..

or
disper
[http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

---

### Post by eyerouge on 2011-08-05
> **BicyclerBoy said:**
> nvidia-settings can be used from the command line & the changes can be immediate.


Ok... how? Everything that handles resolution sees to be read-only according to it. Please share an example where you change your resolution from the cli using nvidia-settings. :)

---

### Post by BicyclerBoy on 2011-08-05
Download the source for nvidia-settings ..
In the mix there is a example/samples folder with program
nv-control-dpy

I believe this shows how...
It may still need xrandr & dynamic twinview metamodes (chapter 13 in the driver readme)

But **disper** looks to do it all...


Here's an old thread detailing building the nv-control-dpy program & with sample control scripts..
[http://ubuntuforums.org/showthread.php?t=922956](http://ubuntuforums.org/showthread.php?t=922956)

---

