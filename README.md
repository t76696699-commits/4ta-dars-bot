import asyncio


async def main():
    # Test uchun namuna indeks va xotira obyektini yaratamiz
    memory = ConversationMemory()
    mock_index = []  # Indeks obyekti

    # 3 bosqichli suhbat ketma-ketligi
    questions = [
        "Python funksiyalari haqida gapirib ber.",
        "Uning parametrlari haqida-chi?",  # Ishora so'zi ishlatilgan savol
        "Unda default qiymatlarni qanday ishlatamiz?",
    ]

    print("=== SUHBAT SINOVI BAŞLANDI ===\n")

    for i, q in enumerate(questions, 1):
        print(f"--- {i}-bosqich ---")
        print(f"Kiritilgan savol: {q}")

        # 1-topshiriq talabi: rewrite_query natijasini konsolga chiqarish
        rewritten = await rewrite_query(q, memory)
        print(f"Qayta yozilgan savol (Rewritten): {rewritten}")

        # Chat funksiyasini chaqirish
        answer, memory = await chat_with_memory(q, memory, mock_index)
        print(f"Javob: {answer}\n")
https://github.com/t76696699/4ta-dars-bot

if __name__ == "__main__":
    asyncio.run(main())
