## Internet TV/Radio Multicast
An IP Multicast model has been implemented socket programming in c.   
Model Flow: 
- Initially by running the `server` program, the server setups 2 multicast groups at different multicast address.
- Both groups have threads running for transmission of data which are active after the setup immediately. 
- When a new client arrives, it receives the available stations present through a **TCP Socket**.
- ON selecting a group, the client immediately starts receiving the data and other stream information through **UDP Sockets** on 2 different threads. 
- The Client can view the video/audio in real time, based on its joining time to the group. 
- Client also has a functionality to pause and play the stream, by keyboard interruption. 
- Multicast group address and ports are fixed in both server and client programmes. 

## Compiling and Running Instructions
- Server   
  - Compiling: `gcc server.c -o server -lpthread`  
  - Running: `./server PORT`
  - `PORT`: Server Port
  - For sending audio/video files from multicast group, the files must be converted into streamable format.   
  It can be done using following command:   
  `ffmpeg -i <inputfilename.extension> -f mpegts <streamable_output.extension>`
  
- Client
  - Compiling: `gcc client.c -o client -lpthread`
  - Running: `sudo ./client SERVER_IP PORT`   
  - `SERVER_IP`: Server IP (`0.0.0.0 / 127.0.0.1` if running in same machine else IP address of Server)   
  - `PORT`: Client Port
  - For Playing the audio/video file received through socket in client, run the following command in new window: `ffplay -i <filename.extension>`
  - For pause operation, press `p` on the terminal receiving the data. It acts as a keyboard interrupt.
  - For restart, press `r` on the terminal.
  
