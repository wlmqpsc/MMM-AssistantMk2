# Developer Notes

## 2019/12/09 -- Bugsounet

- create translation FR / EN for error
- create chime (activate / error / continue) and feature UseChime (true/false)
- create if UsefullScreenAnswer set to false (only show icon)
- correct showmodule (true/false)
- correct little bug with continuous conversation and display
- create script to display status when activeassistant (using types / continous converstation)
- css dispatch fullscreen or not
- send status notification to other modules
- create logo for AMk2 v3 (big and small) 

![](https://raw.githubusercontent.com/eouia/MMM-AssistantMk2/3-dev/resources/AMk2_Small.png)

## 2019/12/08 -- Bugsounet

- write fullscreen css AMK2 v3
- create icon and display style with full animated icons 

## 2019/12/06 -- Bugsounet

- add FullScreenAnswer Feature
- to eouia > correct merge this.config / this.default / this.helperConfig
- temp code to correct this merge

## 2019/12/04 -- Bugsounet

- write main loop
- debug -> continue conversation seems to be ok (see eouia inspection)
- to eouia > can you see MMM-Hotword, afterRecordLimit does not work when there is silence but when there some noise <---- ok issue closed
- ret.key -> change it : ret.key = "modules/MMM-Hotword/" + afterRecord
- create tmp folder -> error when writing tmp file


## 12/06 -- eouia
- Annoying case - `TOO_SHORT` : Usually it happenes when transcription Recognition fails from Google.
```
[AMK2:AS] CONVERSATION:TRANSCRIPTION { transcription: 'how is the way', done: false }
[AMK2:AS] CONVERSATION:TRANSCRIPTION { transcription: 'how is the weather', done: false }
[AMK2:AS] CONVERSATION:RESPONSE
[AMK2:AS] CONVERSATION_ALL_RESPONSES_RECEIVED
[AMK2:AS] CONVERSATION_END:COMPLETED
[AMK2:AS] CONVERSATION_PP:RESPONSE_AUDIO_TOO_SHORT_OR_EMPTY -  50
[AMK2] { session: 1575819784757,
  error: 'TOO_SHORT',
  action: null,
  text: null,
  screen: null,
  audio: null,
  transcription: { transcription: 'how is the weather', done: false },
  continue: false,
  lastQuery:
   { type: 'WAVEFILE',
     profile: { profileFile: 'default.json', lang: 'ko-KR' },
     key:
      '/Users/eouia/Documents/nodeJS/MagicMirror/modules/MMM-Hotword/temp/afterRecording.wav',
     lang: null,
     useScreenOutput: true,
     useAudioOutput: true,
     session: 1575819784757 } }
```
Have you experienced? In this case,(If `TOO_SHORT` && `transcription.done:false` && `transcription.transcription:something not null`), Is it better to query again by TEXT with `transcription.transcription` ?
Bugsounet ->> I have it sometime, i have not inpect this bug