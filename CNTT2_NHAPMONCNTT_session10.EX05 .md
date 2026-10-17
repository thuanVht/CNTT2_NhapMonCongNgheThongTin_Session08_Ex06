---


---

<h3 id="phần-1-phân-tích-kiến-trúc-hệ-thống-bước-1">PHẦN 1: PHÂN TÍCH KIẾN TRÚC HỆ THỐNG (BƯỚC 1)</h3>
<p><strong>1. Mô hình IPO (Input - Process - Output)</strong></p>
<ul>
<li>
<p><strong>Input (Đầu vào):</strong> Cảm biến độ ẩm đất, cảm biến nhiệt độ &amp; độ ẩm không khí (DHT22), cảm biến ánh sáng (BH1750).</p>
</li>
<li>
<p><strong>Process (Xử lý):</strong> Vi điều khiển SoC (ESP32/Raspberry Pi) đọc dữ liệu, đối chiếu ngưỡng cài đặt và ra quyết định.</p>
</li>
<li>
<p><strong>Output (Đầu ra):</strong> Module rơ-le kích hoạt máy bơm phun sương tưới lan và màn hình hiển thị.</p>
</li>
</ul>
<p><strong>2. Sơ đồ phối hợp phần cứng</strong><br>
Plaintext<br>
[Cảm biến môi trường] ──(Dữ liệu)──&gt; [SoC / ESP32]<br>
│<br>
(Ra lệnh bật/tắt)<br>
│<br>
▼<br>
[Máy bơm tưới lan] &lt;──(Đóng mạch)── [Module Rơ-le].</p>
<h2 id="section"></h2>
<h3 id="phần-2-file-readme.md">PHẦN 2: FILE <a href="http://README.MD">README.MD</a></h3>
<h1 id="hệ-thống-giám-sát-và-tưới-lan-tự-động-smart-farm-iot">HỆ THỐNG GIÁM SÁT VÀ TƯỚI LAN TỰ ĐỘNG (SMART-FARM IOT)</h1>
<blockquote>
<p><em>Hệ thống tự động hóa nông nghiệp thông minh giúp tối ưu lượng nước tưới, theo dõi môi trường thời gian thực và bảo vệ vườn lan tối đa.</em></p>
</blockquote>
<hr>
<h2 id="sơ-đồ-kiến-trúc-hệ-thống">1. Sơ đồ kiến trúc hệ thống</h2>
<p><img src="https://svgshare.com/i/15y0.svg" alt="Sơ đồ kiến trúc kết nối cảm biến, bộ xử lý SoC và thiết bị tưới lan"></p>
<hr>
<h2 id="bảng-thông-số-kỹ-thuật-phần-cứng">2. Bảng thông số kỹ thuật phần cứng</h2>

<table>
<thead>
<tr>
<th align="left">Thiết bị / Lớp</th>
<th align="left">Tên linh kiện</th>
<th align="left">Thông số kỹ thuật</th>
<th align="left">Vai trò trong hệ thống</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><strong>SoC / Controller</strong></td>
<td align="left">ESP32 WROOM</td>
<td align="left">Dual-core 240MHz, Wi-Fi &amp; BLE</td>
<td align="left">Bộ xử lý trung tâm</td>
</tr>
<tr>
<td align="left"><strong>Input Sensor</strong></td>
<td align="left">DHT22 &amp; Soil Moisture</td>
<td align="left">Đo nhiệt độ (-40-80°C), độ ẩm đất</td>
<td align="left">Thu thập dữ liệu môi trường</td>
</tr>
<tr>
<td align="left"><strong>Output Actuator</strong></td>
<td align="left">Rơ-le 4 kênh 5V</td>
<td align="left">Cách ly quang, chịu tải 10A/250VAC</td>
<td align="left">Điều khiển máy bơm tưới lan</td>
</tr>
</tbody>
</table><hr>
<h2 id="tính-năng-chính-của-hệ-thống">3. Tính năng chính của hệ thống</h2>
<ul>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Tự động đo nhiệt độ, độ ẩm không khí và độ ẩm đất theo chu kỳ 5 giây/lần.</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Tự động bật máy bơm phun sương khi đất khô hoặc nhiệt độ vượt ngưỡng.</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Gửi cảnh báo về điện thoại khi có sự cố mất nước hoặc lỗi cảm biến.</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Tính năng nâng cao: Dự báo sâu bệnh dựa trên lịch sử độ ẩm (Đang phát triển).</li>
</ul>
<hr>
<h2 id="hướng-dẫn-cài-đặt-và-vận-hành">4. Hướng dẫn cài đặt và Vận hành</h2>
<p>BASH</p>
<h1 id="tải-mã-nguồn-hệ-thống-về-máy-chủ">1. Tải mã nguồn hệ thống về máy chủ</h1>
<p>git clone <a href="https://github.com/smart-farm/lan-irrigation.git">https://github.com/smart-farm/lan-irrigation.git</a></p>
<h1 id="truy-cập-thư-mục-dự-án">2. Truy cập thư mục dự án</h1>
<p>cd lan-irrigation</p>
<h1 id="cài-đặt-các-thư-viện-phụ-thuộc">3. Cài đặt các thư viện phụ thuộc</h1>
<p>pip install -r requirements.txt</p>
<h1 id="khởi-chạy-hệ-thống-giám-sát">4. Khởi chạy hệ thống giám sát</h1>
<p>python3 <a href="http://main.py">main.py</a>.</p>
<h2 id="section-1"></h2>
<pre><code>       / \
      /   \     [WISDOM] Tự động tưới 5 phút lúc 12h trưa để làm mát vườn.
     /  W  \
    /-------\   [KNOWLEDGE] Đất khô kết hợp nắng gắt làm lá héo rễ.
   /    K    \
  /-----------\ [INFORMATION] Độ ẩm đất = 35% (Ngưỡng thiếu nước &lt; 50%).
 /      I      \
/---------------\ [DATA] Nhiệt độ: 36.5°C | Độ ẩm đất: 35%.

</code></pre>
<h2 id="lưu-ý-và-xử-lý-sự-cố-kỹ-thuật">6. Lưu ý và Xử lý sự cố kỹ thuật</h2>
<ul>
<li>
<p><strong>Bảo trì cảm biến:</strong> Vệ sinh đầu đo độ ẩm đất 3 tháng/lần để tránh sai số.</p>
</li>
<li>
<p><strong>Xử lý RAM bị đầy do nhật ký (Log Buffer Overflow):</strong></p>
<ul>
<li>
<p><em>Hiện tượng:</em> Hệ thống đơ, không bật bơm do RAM chứa quá nhiều file log tạm thời.</p>
</li>
<li>
<p><em>Cách khắc phục:</em> Nhấn nút Reset cứng trên bo mạch hoặc chạy lệnh xóa log qua terminal:</p>
<p>Bash</p>
<pre><code>sudo sync &amp;&amp; echo 3 | sudo tee /proc/sys/vm/drop_caches
rm -rf /tmp/farm_logs/*
</code></pre>
</li>
</ul>
</li>
</ul>

