<template>
    <div class="page">
        <h4>Thêm Liên hệ</h4>
        <ContactForm @submit:contact="createContact" />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            message: "",
        };
    },
    methods: {
        async createContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Tạo liên hệ thành công!!!";
            } catch (err) {
                console.log(err);
            }
        },
    },
    async created() {
        this.message = "";
    },
};
</script>