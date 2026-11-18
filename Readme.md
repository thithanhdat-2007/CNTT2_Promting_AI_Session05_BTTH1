# BÀI TẬP: LẬP KẾ HOẠCH TÀI CHÍNH CÁ NHÂN BẰNG KỸ THUẬT CHAIN-OF-THOUGHT (CoT)

## PHẦN A: BẢN THIẾT KẾ PROMPT HOÀN CHỈNH (MASTER PROMPT)

Dưới đây là cấu trúc Prompt được thiết kế thuần túy bằng ngôn ngữ tự nhiên (Prompting Logic), kết hợp khung **CREATE** và kỹ thuật **Structured Chain-of-Thought** để kiểm soát chặt chẽ từng phép tính số học của AI.

---

### [NỘI DUNG PROMPT ĐƯA VÀO AI]

**1. Vai trò (Character):**
Bạn là một Chuyên gia Hoạch định Tài chính Cá nhân (Certified Financial Planner) có khả năng tính toán số học chính xác tuyệt đối. Nhiệm vụ của bạn là lập kế hoạch phân bổ dòng tiền hàng tháng cho khách hàng có thu nhập biến động và đang mang nợ, đảm bảo tối ưu hóa việc trả nợ, duy trì kỷ luật tiết kiệm và cân bằng chi tiêu.

**2. Dữ liệu đầu vào (Input Data):**
Hãy lập kế hoạch tài chính dựa trên thông số tháng hiện tại của khách hàng như sau:
* **Tổng thu nhập tháng này (Gross Income):** `[Nhập tổng thu nhập, ví dụ: 30.000.000 VNĐ]`
* **Thuế và Bảo hiểm bắt buộc:** `[Nhập số tiền hoặc %, ví dụ: 5% tổng thu nhập = 1.500.000 VNĐ]`
* **Chi phí cố định bắt buộc (thuê nhà, điện nước, ăn uống cơ bản):** `[Nhập số tiền, ví dụ: 9.000.000 VNĐ]`
* **Các khoản nợ cần thanh toán:** `[Nhập danh sách nợ và mức trả tối thiểu, ví dụ: Nợ thẻ tín dụng tối thiểu 3.000.000 VNĐ; Trả góp vay tiêu dùng 3.000.000 VNĐ]`
* **Mục tiêu tiết kiệm cam kết (tối thiểu $20\%$ tổng thu nhập):** `[Nhập tỷ lệ, ví dụ: 15% Tiết kiệm dài hạn + 5% Quỹ dự phòng khẩn cấp]`

**3. Quy trình suy luận bắt buộc (Chain-of-Thought Instruction):**
**Hãy suy nghĩ từng bước một và tính toán chi tiết trước khi đưa ra quyết định.**

Bạn bắt buộc phải thực hiện tuần tự 4 bước lập luận dưới đây, viết rõ từng công thức và phép tính trung gian ($+$, $-$, $\times$, $\div$), tuyệt đối không tính nhẩm hoặc nhảy cóc qua bước:

* **Bước 1: Tính toán tổng thu nhập khả dụng sau khi trừ thuế và chi phí cố định bắt buộc.**
  * Liệt kê Tổng thu nhập ban đầu ($100\%$).
  * Thực hiện phép trừ: $\text{Thu nhập khả dụng} = \text{Tổng thu nhập} - \text{Thuế \& Bảo hiểm} - \text{Chi phí cố định bắt buộc}$.
  * Tính tỷ lệ phần trăm tương ứng của từng khoản trên Tổng thu nhập theo công thức: $\text{Tỷ lệ \%} = (\text{Số tiền hạng mục} \div \text{Tổng thu nhập}) \times 100\%$.

* **Bước 2: Phân bổ khoản tiền trả nợ tối thiểu.**
  * Cộng tất cả các khoản trả nợ tối thiểu bắt buộc trong tháng để tránh phí phạt và nợ xấu.
  * Thực hiện phép trừ để tìm số dư sau trả nợ: $\text{Số dư sau trả nợ} = \text{Thu nhập khả dụng (Bước 1)} - \text{Tổng nợ tối thiểu}$.
  * Tính tỷ lệ phần trăm của khoản trả nợ tối thiểu so với Tổng thu nhập.

* **Bước 3: Trích lập quỹ tiết kiệm theo tỷ lệ cam kết.**
  * Kiểm tra điều kiện: Tổng tỷ lệ trích lập tiết kiệm và quỹ dự phòng khẩn cấp phải đạt tối thiểu $20\%$ Tổng thu nhập.
  * Tính số tiền tiết kiệm và quỹ dự phòng cụ thể bằng phép nhân: $\text{Số tiền tiết kiệm} = \text{Tổng thu nhập} \times \text{Tỷ lệ cam kết}$.
  * Thực hiện phép trừ để tìm ngân sách còn lại: $\text{Ngân sách còn lại} = \text{Số dư sau trả nợ (Bước 2)} - \text{Tổng tiền tiết kiệm \& dự phòng}$.

* **Bước 4: Chia phần còn lại cho chi tiêu linh hoạt theo quy tắc 50/30/20 cải tiến.**
  * Lấy toàn bộ $\text{Ngân sách còn lại}$ ở Bước 3 làm quỹ phân bổ linh hoạt và chia theo tỷ lệ 50/30/20 cải tiến dành cho người có thu nhập biến động đang trả nợ:
    * $50\%$ $\text{Ngân sách còn lại}$: Trả thêm nợ gốc lãi suất cao và Đầu tư phát triển bản thân.
    * $30\%$ $\text{Ngân sách còn lại}$: Chi tiêu linh hoạt, giải trí cá nhân.
    * $20\%$ $\text{Ngân sách còn lại}$: Quỹ đệm bù đắp biến động thu nhập cho tháng sau.
  * Quy đổi từng khoản này sang số tiền cụ thể và tỷ lệ phần trăm trên Tổng thu nhập ban đầu.
  * **Bước kiểm산 (Self-Check):** Cộng tổng tất cả số tiền của các hạng mục và cộng tổng tất cả tỷ lệ phần trăm để đảm bảo khớp chính xác $100\%$ Tổng thu nhập ban đầu.

**4. Định dạng kết quả đầu ra (Output Format):**
Trình bày câu trả lời thành 2 phần rõ rệt:
* **Phần 1: Nhật ký suy luận logic (Reasoning Steps):** Trình bày đầy đủ công thức, phép tính cộng trừ nhân chia trung gian và số liệu của cả 4 bước cùng bước kiểm tra tổng.
* **Phần 2: Bảng phân bổ ngân sách cuối cùng:** Xuất bảng Markdown Table gồm đúng 4 cột: `Hạng mục` | `Số tiền` | `Tỷ lệ %` | `Ghi chú`. Hàng cuối cùng của bảng là hàng `TỔNG CỘNG` phải đạt chính xác $100\%$.

**5. Ràng buộc kỹ thuật (Constraints):**
* Không sử dụng code Python, Pydantic hay bất kỳ ngôn ngữ lập trình nào; giải quyết hoàn toàn bằng lập luận ngôn ngữ và toán học từng bước.
* Hiển thị tường minh mọi phép tính trung gian (ví dụ: viết rõ $30,000,000 - 1,500,000 - 9,000,000 = 19,500,000$, không chỉ ghi mỗi kết quả $19,500,000$).
* Tổng tỷ lệ phần trăm phân bổ ngân sách ở bảng cuối cùng bắt buộc bằng chính xác $100\%$.

---

## PHẦN B: KẾT QUẢ CHẠY THỬ NGHIỆM MẪU (SIMULATED AI OUTPUT)

Dưới đây là kết quả đầu ra chuẩn xác khi đưa Prompt trên vào LLM với bộ dữ liệu mẫu: Tổng thu nhập $30,000,000\text{ VNĐ}$, Thuế & Bảo hiểm $1,500,000\text{ VNĐ}$, Chi phí cố định $9,000,000\text{ VNĐ}$, Nợ tối thiểu $6,000,000\text{ VNĐ}$, Mục tiêu tiết kiệm $20\%$ ($15\%$ tiết kiệm dài hạn + $5\%$ quỹ dự phòng).

### Phần 1: Nhật ký suy luận logic (Reasoning Steps)

Thực hiện suy nghĩ từng bước một và tính toán chi tiết trước khi đưa ra quyết định:

* **Bước 1: Tính toán tổng thu nhập khả dụng sau khi trừ thuế và chi phí cố định bắt buộc**
  * Tổng thu nhập tháng hiện tại: $30,000,000\text{ VNĐ}$ (tương ứng $100\%$).
  * Trừ khoản Thuế và Bảo hiểm bắt buộc: $1,500,000\text{ VNĐ}$.
    * Tỷ lệ trên tổng thu nhập: $(1,500,000 \div 30,000,000) \times 100\% = 0.05 \times 100\% = 5.0\%$.
  * Trừ khoản Chi phí cố định bắt buộc (thuê nhà, điện nước, ăn uống cơ bản): $9,000,000\text{ VNĐ}$.
    * Tỷ lệ trên tổng thu nhập: $(9,000,000 \div 30,000,000) \times 100\% = 0.30 \times 100\% = 30.0\%$.
  * Phép tính Thu nhập khả dụng còn lại:
    $$\text{Thu nhập khả dụng} = 30,000,000 - 1,500,000 - 9,000,000 = 19,500,000\text{ VNĐ}$$
  * Tỷ lệ Thu nhập khả dụng còn lại: $100\% - 5.0\% - 30.0\% = 65.0\%$.

* **Bước 2: Phân bổ khoản tiền trả nợ tối thiểu**
  * Tổng hợp các khoản nợ phải trả tối thiểu đúng hạn:
    $$\text{Tổng nợ tối thiểu} = 3,000,000\text{ (Thẻ tín dụng)} + 3,000,000\text{ (Vay tiêu dùng)} = 6,000,000\text{ VNĐ}$$
  * Tỷ lệ trả nợ tối thiểu trên tổng thu nhập:
    $$(6,000,000 \div 30,000,000) \times 100\% = 0.20 \times 100\% = 20.0\%$$
  * Phép tính Số dư còn lại sau khi trả nợ tối thiểu:
    $$\text{Số dư sau trả nợ} = 19,500,000 - 6,000,000 = 13,500,000\text{ VNĐ}$$
  * Tỷ lệ số dư còn lại: $65.0\% - 20.0\% = 45.0\%$.

* **Bước 3: Trích lập quỹ tiết kiệm theo tỷ lệ cam kết (Tối thiểu $20\%$)**
  * Quỹ tiết kiệm dài hạn ($15\%$ tổng thu nhập):
    $$30,000,000 \times 15\% = 30,000,000 \times 0.15 = 4,500,000\text{ VNĐ}$$
  * Quỹ dự phòng khẩn cấp ($5\%$ tổng thu nhập):
    $$30,000,000 \times 5\% = 30,000,000 \times 0.05 = 1,500,000\text{ VNĐ}$$
  * Tổng trích lập tiết kiệm và dự phòng:
    $$4,500,000 + 1,500,000 = 6,000,000\text{ VNĐ}\text{ (Đạt chuẩn } 15\% + 5\% = 20.0\%\text{)}$$
  * Phép tính Ngân sách còn lại cho chi tiêu linh hoạt:
    $$\text{Ngân sách còn lại} = 13,500,000 - 6,000,000 = 7,500,000\text{ VNĐ}$$
  * Tỷ lệ Ngân sách còn lại: $45.0\% - 20.0\% = 25.0\%$.

* **Bước 4: Chia phần còn lại ($7,500,000\text{ VNĐ}$) theo quy tắc 50/30/20 cải tiến**
  * **Nhóm 1 ($50\%$ ngân sách còn lại) - Trả thêm nợ gốc lãi cao & Phát triển bản thân:**
    * Số tiền: $7,500,000 \times 50\% = 7,500,000 \times 0.50 = 3,750,000\text{ VNĐ}$.
    * Tỷ lệ trên tổng thu nhập: $(3,750,000 \div 30,000,000) \times 100\% = 0.125 \times 100\% = 12.5\%$.
  * **Nhóm 2 ($30\%$ ngân sách còn lại) - Chi tiêu linh hoạt & Giải trí cá nhân:**
    * Số tiền: $7,500,000 \times 30\% = 7,500,000 \times 0.30 = 2,250,000\text{ VNĐ}$.
    * Tỷ lệ trên tổng thu nhập: $(2,250,000 \div 30,000,000) \times 100\% = 0.075 \times 100\% = 7.5\%$.
  * **Nhóm 3 ($20\%$ ngân sách còn lại) - Quỹ đệm biến động thu nhập tháng sau:**
    * Số tiền: $7,500,000 \times 20\% = 7,500,000 \times 0.20 = 1,500,000\text{ VNĐ}$.
    * Tỷ lệ trên tổng thu nhập: $(1,500,000 \div 30,000,000) \times 100\% = 0.05 \times 100\% = 5.0\%$.

* **Bước kiểm tra tổng thể (Verification Step):**
  * Kiểm tra tổng số tiền phân bổ:
    $$1,500,000 + 9,000,000 + 6,000,000 + 4,500,000 + 1,500,000 + 3,750,000 + 2,250,000 + 1,500,000 = 30,000,000\text{ VNĐ}$$
  * Kiểm tra tổng tỷ lệ phần trăm:
    $$5.0\% + 30.0\% + 20.0\% + 15.0\% + 5.0\% + 12.5\% + 7.5\% + 5.0\% = 100.0\%$$

### Phần 2: Bảng phân bổ ngân sách cuối cùng

| Hạng mục | Số tiền | Tỷ lệ % | Ghi chú |
| :--- | :--- | :--- | :--- |
| Thuế & Bảo hiểm | 1.500.000 VNĐ | 5.0% | Khấu trừ bắt buộc |
| Chi phí cố định | 9.000.000 VNĐ | 30.0% | Nhà ở, ăn uống |
| Trả nợ tối thiểu | 6.000.000 VNĐ | 20.0% | Trả đúng hạn |
| Tiết kiệm dài hạn | 4.500.000 VNĐ | 15.0% | Tích lũy cố định |
| Quỹ dự phòng | 1.500.000 VNĐ | 5.0% | Khẩn cấp y tế |
| Trả nợ thêm | 3.750.000 VNĐ | 12.5% | 50% phần dư |
| Chi tiêu giải trí | 2.250.000 VNĐ | 7.5% | 30% phần dư |
| Quỹ đệm thu nhập | 1.500.000 VNĐ | 5.0% | 20% phần dư |
| **TỔNG CỘNG** | **30.000.000 VNĐ** | **100.0%** | **Cân bằng hoàn toàn** |

**Giải thích chiến lược phân bổ:**
* **Đảm bảo kỷ luật tài chính:** Khoản tiết kiệm dài hạn ($15\%$) và quỹ dự phòng khẩn cấp ($5\%$) được trích lập ngay ở Bước 3 (đạt đúng cam kết $20\%$) trước khi chi tiêu linh hoạt, giúp hình thành thói quen trả cho bản thân trước.
* **Tối ưu hóa tốc độ thoát nợ:** Nhờ trích thêm $50\%$ số dư linh hoạt ($3,750,000\text{ VNĐ}$) để tất toán sớm nợ gốc lãi cao (như dư nợ thẻ tín dụng), tổng ngân sách dành cho việc xử lý nợ trong tháng đạt $32.5\%$, rút ngắn đáng kể thời gian trả nợ.
* **Chống sốc thu nhập biến động:** Khoản quỹ đệm $5.0\%$ ($1,500,000\text{ VNĐ}$) giữ vai trò bù đắp cho những tháng thu nhập sụt giảm mà không làm ảnh hưởng đến quỹ dự phòng khẩn cấp.