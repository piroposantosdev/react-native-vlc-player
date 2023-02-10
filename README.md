# react-native-vlc-media-player

<!---Esses são exemplos. Veja https://shields.io para outras pessoas ou para personalizar este conjunto de escudos. Você pode querer incluir dependências, status do projeto e informações de licença aqui--->

![GitHub repo size](https://img.shields.io/github/repo-size/piroposantosdev/react-native-vlc-player?style=for-the-badge)
![GitHub language count](https://img.shields.io/github/languages/count/piroposantosdev/react-native-vlc-player?style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/piroposantosdev/react-native-vlc-player?style=for-the-badge)
![Bitbucket open issues](https://img.shields.io/bitbucket/issues/piroposantosdev/react-native-vlc-player?style=for-the-badge)
![Bitbucket open pull requests](https://img.shields.io/bitbucket/pr-raw/piroposantosdev/react-native-vlc-player?style=for-the-badge)

> Working in RN 0.69 adapted by Andre Piropo Santos
> This project is a simple nodejs method to get a list of all embassy worldwide. <br>
> All embassies are retrieved from https://www.embassy-worldwide.com/. <br>
> The project uses puppeteer plugin to access the page, retrieve all data and store each embassy in a folder. Inside each folder (named with embassy name) there is two txt files called "Embassy Name + in or out", inside this files there are all coutries that there is relationship with that embassy.<br>
> Embassy Name-in means all embassies there are in that country;<br>
> OBS.: Material Icons Font not included... you must add it by yourself in your project. You must disable bitcode from your project build settings to work.<br>
> 0.59 > 0.62 and up <br>
> PODs are updated to works with 0.61 and up.(Tested in 0.61.5 and 0.62 and 0.63)

## 📁 Sample Repo

[VLC Media Player Sample](https://github.com/razorRun/react-native-vlc-media-player-test)

## 💻 Supported formats

Before you begin, keep the following notes in mind:
<!---Estes são apenas requisitos de exemplo. Adicionar, duplicar ou remover conforme necessário--->
* Support for network streams, RTSP, RTP, RTMP, HLS, MMS. Play all files, in all formats, including exotic ones, like the classic VLC media player. Play MKV, multiple audio tracks (including 5.1), and subtitles tracks (including SSA!)

## 🚀 Install react-native-vlc-media-player

To install react-native-vlc-media-player, follow these steps:<br>

Run

```
1. npm i https://github.com/piroposantosdev/react-native-vlc-player.git --save 
or 
yarn add https://github.com/piroposantosdev/react-native-vlc-player.git

2. For IOS app:
  2.1. cd to ios
  2.2. run pod init (if only Podfile has not been generated in ios folder)
  2.3. add pod 'MobileVLCKit', '3.3.10' to pod file (No need if you are running RN 0.61 and up)
  2.4. run pod install (you have to delete the app on the simulator/device and run react-native run-ios again)

3. For Android APP:
  3.1. Maybe you will found an error when try to build for Android, something like this "2 files found with path 'lib/arm64-v8a/libc++_shared.so' from inputs...-react native... 
  3.1.1. To solve this problem, follow this steps... 
        1 - Go to android/app/build.gradle file... 
        2 - Add this to android{ ... }
        
        //Where add
        android { 
          //Add this lines below
          packagingOptions {
            pickFirst 'lib/x86/libc++_shared.so'
            pickFirst 'lib/arm64-v8a/libc++_shared.so'
            pickFirst 'lib/x86_64/libc++_shared.so'
            pickFirst 'lib/armeabi-v7a/libc++_shared.so'
          }
          //End
        }

4. Optional (IOS ONLY) 
  4.1. Enable Bitcode in root project select Build Settings ---> find Bitcode and select Enable Bitcode
```

## ⌛ Usage
```
  import { VLCPlayer, VlCPlayerView } from 'react-native-vlc-media-player';
  import Orientation from 'react-native-orientation';

  <VLCPlayer
      style={[styles.video]}
      videoAspectRatio="16:9"
      source={{ uri: "https://www.radiantmediaplayer.com/media/big-buck-bunny-360p.mp4"}}
  />

  or

  <VlCPlayerView
    autoplay={false}
    url="https://www.radiantmediaplayer.com/media/big-buck-bunny-360p.mp4"
    Orientation={Orientation}
    ggUrl=""
    showGG={true}
    showTitle={true}
    title="Big Buck Bunny"
    showBack={true}
    onLeftPress={()=>{}}
  />
```

## 🔍 VLCPlayer Props

Prop | Description | Default
---- | ----------- | -------
`source` | Object that contains the uri of a video or song to play eg `{{ uri: "https://video.com/example.mkv" }}` | `{}`
`paused` | Set to `true` or `false` to pause or play the media | `false`
`repeat` | Set to `true` or `false` to loop the media | `false`
`rate` | Set the playback rate of the player| `1`
`seek` | Set position to seek between `0` and `1` (`0` being the start, `1` being the end , use `position` from the progress object )
`volume` | Set the volume of the player (`number`)
`muted` | Set to `true` or `false` to mute the player |  `false`
`playInBackground` | Set to `true` or `false` to allow playing in the background | false
`videoAspectRatio ` | Set the video aspect ratio eg `"16:9"`
`autoAspectRatio` | Set to `true` or `false` to enable auto aspect ratio | false
`resizeMode` | Set the behavior for the video size (`fill, contain, cover, none, scale-down`) | none
`style` | React native stylesheet styles| `{}`

## 🖥 Callback props

Callback props take a function that gets fired on various player events:

Prop | Description
---- | -----------
`onPlaying` | Called when media starts playing returns eg `{target: 9, duration: 99750, seekable: true}`
`onProgress` | Callback containing `position` as a fraction, and `duration`, `currentTime` and `remainingTime` in seconds <br />&nbsp; ◦ &nbsp;eg `{  duration: 99750, position: 0.30, currentTime: 30154, remainingTime: -69594 }`
`onPaused` | Called when media is paused
`onStopped ` | Called when media is stoped
`onBuffering ` | Called when media is buffering
`onEnded` | Called when media playing ends
`onError` | Called when an error occurs whilst attempting to play media


## ➕ More formats

Container formats: 3GP, ASF, AVI, DVR-MS, FLV, Matroska (MKV), MIDI, QuickTime File Format, MP4, Ogg, OGM, WAV, MPEG-2 (ES, PS, TS, PVA, MP3), AIFF, Raw audio, Raw DV, MXF, VOB, RM, Blu-ray, DVD-Video, VCD, SVCD, CD Audio, DVB, HEIF, AVIF
Audio coding formats: AAC, AC3, ALAC, AMR, DTS, DV Audio, XM, FLAC, It, MACE, MOD, Monkey's Audio, MP3, Opus, PLS, QCP, QDM2/QDMC, RealAudio, Speex, Screamtracker 3/S3M, TTA, Vorbis, WavPack, WMA (WMA 1/2, WMA 3 partially).
Capture devices: Video4Linux (on Linux), DirectShow (on Windows), Desktop (screencast), Digital TV (DVB-C, DVB-S, DVB-T, DVB-S2, DVB-T2, ATSC, Clear QAM)
Network protocols: FTP, HTTP, MMS, RSS/Atom, RTMP, RTP (unicast or multicast), RTSP, UDP, Sat-IP, Smooth Streaming
Network streaming formats: Apple HLS, Flash RTMP, MPEG-DASH, MPEG Transport Stream, RTP/RTSP ISMA/3GPP PSS, Windows Media MMS
Subtitles: Advanced SubStation Alpha, Closed Captions, DVB, DVD-Video, MPEG-4 Timed Text, MPL2, OGM, SubStation Alpha, SubRip, SVCD, Teletext, Text file, VobSub, WebVTT, TTML
Video coding formats: Cinepak, Dirac, DV, H.263, H.264/MPEG-4 AVC, H.265/MPEG HEVC, AV1, HuffYUV, Indeo 3, MJPEG, MPEG-1, MPEG-2, MPEG-4 Part 2, RealVideo 3&4, Sorenson, Theora, VC-1,[h] VP5, VP6, VP8, VP9, DNxHD, ProRes and some WMV.


## 🤝 Collaborators

Agradecemos às seguintes pessoas que contribuíram para este projeto:

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/ammarahm-ed" target="_blank">        
        <sub>
          <b>ammarahm-ed</b>
        </sub>
      </a>
    </td> 
    <td align="center">
      <a href="https://github.com/Nghi-NV" target="_blank">        
        <sub>
          <b>Nghi-NV</b>
        </sub>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/xuyuanzhou" target="_blank">        
        <sub>
          <b>xuyuanzhou</b>
        </sub>
      </a>
    </td>   
  </tr>
</table>

## 📝 License

This design is free to use.

[⬆ Voltar ao topo](#readme)<br>
